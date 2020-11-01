<template>
  <div id="container">
    <div v-if="articles">
      <ion-col size="4" v-for="article in articles" :key="article.id">
      <ion-card>
        <ion-card-header>
          <ion-card-subtitle>{{article.published_at}}</ion-card-subtitle>
          <ion-card-title>{{article.title}}</ion-card-title>
        </ion-card-header>
        
        <ion-card-content>
          <ion-item>
            <ion-thumbnail slot="start">
             <img :src="article.feature_image">
            </ion-thumbnail>
            {{article.excerpt}}
          </ion-item>
        
        </ion-card-content>
      </ion-card>
      </ion-col>
    </div>
  </div>
</template>

<script lang="ts">
import { IonCol, IonCard, IonItem, IonCardHeader, IonThumbnail, IonCardContent, IonCardSubtitle, IonCardTitle} from '@ionic/vue';
import axios from 'axios';
import { ref } from 'vue';
export default {
  name: 'FeaturedArticles',
  components: { IonCol, IonCard, IonItem, IonCardHeader, IonThumbnail, IonCardContent, IonCardSubtitle, IonCardTitle },

  // api : https://cms.resurgentindia.org/ghost/api/v3/content/posts/?key=17e77de2cd693395fa6f1ecdb9
  setup(){
    const articles: any = ref([]);
    axios.get('https://cms.resurgentindia.org/ghost/api/v3/content/posts/?key=17e77de2cd693395fa6f1ecdb9').then(res =>{
      articles.value = res.data.posts
    })
    console.log(articles)
    return {
      articles
    }
  }
  
}
</script>

<style scoped>
#container {
  left: 0;
  right: 0;
  text-align: justify;
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
  text-align:justify;
}

#container a {
  text-decoration: none;
}
</style>