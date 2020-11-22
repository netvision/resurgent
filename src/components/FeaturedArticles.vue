<template>
    <div id="featured" v-if="articles" class="ion-padding">
        <h2>Featured Articles</h2>
        <vueper-slides class="no-shadow" transition-speed="250" :3d="true" :bulletsOutside="true">
          <vueper-slide v-for="(article, i) in articles" :key="i" :title="article.title" content="Click to read..." :image="article.feature_image" :link="'article/'+article.id" />
        </vueper-slides>
    </div> 
  
</template>

<script lang="ts">
import 'vueperslides/dist/vueperslides.css'
//import { IonGrid, IonRow, IonCol, IonImg} from '@ionic/vue';
import axios from 'axios';
import { ref } from 'vue';
import { VueperSlides, VueperSlide } from 'vueperslides';
//import { BuildInfo } from '@ionic-native/build-info';

export default {
  
  name: 'FeaturedArticles',
  components: { VueperSlides, VueperSlide },

  // api : https://cms.resurgentindia.org/ghost/api/v3/content/posts/?key=17e77de2cd693395fa6f1ecdb9
  setup(){
    const articles: any = ref([]);
    
    axios.get('https://cms.resurgentindia.org/ghost/api/v3/content/posts/?key=17e77de2cd693395fa6f1ecdb9&fields=id,title,excerpt,feature_image,published_at&filter=featured:true&limit=5&order=published_at%20desc').then(res =>{
      articles.value = res.data.posts;
    });
    return {
      articles,
      
    }
  }
  
}
</script>

<style>
#featured .vueperslide__content-wrapper
{
  font-family: inherit;
-webkit-box-pack: end;
-ms-flex-pack: end;
justify-content: flex-end;
-webkit-box-align: end;
-ms-flex-align: end;
align-items: flex-end;
opacity: .8;
padding-bottom: 1em;
padding-right: 1.5em;
padding-left: 10%;
}

#featured .vueperslide__title{
  font-size: 1.5em;
  line-height: 1.3;  
  background-color: antiquewhite;
}

#featured .vueperslide__content{
  font-style: italic;
  position: relative;
  background-color: antiquewhite;
}

h2{
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    font-weight: bold;
    align-self: start;
    border-bottom: coral 1px solid;
}
</style>