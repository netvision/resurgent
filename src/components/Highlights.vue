<template>
    <div id="highlights" v-if="highlights" class="ion-padding">
        <ion-list>
            <ion-list-header>
            <h2>Recent Highlights</h2>
            </ion-list-header>

            <ion-item v-for="(highlight, i) in highlights" :key="i" :router-link="`/article/${highlight.id}`" class="ion-align-items-start">
                <ion-thumbnail slot="start" style="padding-top:10px">
                    <img :src="highlight.feature_image"> 
                </ion-thumbnail>
                <ion-label class="ion-text-wrap">
                    <h2>{{highlight.title}}</h2>
                    <p>{{highlight.custom_excerpt}}</p>
                </ion-label>
            </ion-item>
        </ion-list>
        
    </div> 
  
</template>

<script lang="ts">
//import 'vueperslides/dist/vueperslides.css'
import { IonList, IonListHeader, IonItem, IonThumbnail, IonLabel} from '@ionic/vue';
import axios from 'axios';
import { ref } from 'vue';
//import { BuildInfo } from '@ionic-native/build-info';

export default {
  
  name: 'Highlights',
  components:{IonList, IonListHeader, IonItem, IonThumbnail, IonLabel},

  // api : https://cms.resurgentindia.org/ghost/api/v3/content/posts/?key=17e77de2cd693395fa6f1ecdb9
  setup(){
    const highlights: any = ref([]);
    
    axios.get('https://cms.resurgentindia.org/ghost/api/v3/content/posts/?key=17e77de2cd693395fa6f1ecdb9&fields=id,title,custom_excerpt,feature_image,published_at&filter=tag:hash-headlines&limit=5&order=published_at%20desc').then(res =>{
      highlights.value = res.data.posts;
    });
    return {
      highlights,
      
    }
  }
  
}
</script>

<style>
#highlights h2{
    font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
    font-weight: bold;
    align-self: start;
    border-bottom: coral 1px solid;
}
#highlights ion-label h2{
    border:none;
}
</style>