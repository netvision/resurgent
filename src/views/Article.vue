<template>
    <ion-page>
        <ion-header>
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-back-button v-if="ionRouter.canGoBack()" default-href="home"></ion-back-button>
                </ion-buttons>
                <img src="http://new.resurgentindia.org/wp-content/uploads/2014/05/resurgentindia-copy11.png" />
                <ion-buttons slot="end">
                    <ion-button v-on:click="fontSize += 0.25" text>
                        A+
                    </ion-button>
                    <ion-button v-on:click="fontSize < 0.5? fontSize = 0.25: fontSize -= 0.25" text>
                        A-
                    </ion-button>
                </ion-buttons>
                 
        
            </ion-toolbar>
        </ion-header>
        <ion-content  class="ion-padding" v-bind:style="{ fontSize: fontSize + 'rem' }">
            <h2>{{art.title}}</h2>
            <ion-img :src="art.feature_image"></ion-img>
            <div class="article-body" v-html="art.html" ></div>
        </ion-content>
    </ion-page>
</template>
<script lang="ts">
import { IonContent, IonPage, IonToolbar, IonHeader, IonButtons, IonBackButton, IonButton, IonImg } from '@ionic/vue';
import { useRoute } from 'vue-router';
import { useIonRouter } from '@ionic/vue';
import { personCircle, search } from 'ionicons/icons';
import axios from 'axios';
import { ref } from 'vue';
export default {
  name: 'Article',
  components: { IonPage, IonToolbar, IonHeader, IonContent, IonButtons, IonBackButton, IonButton, IonImg },
  data(){
      return{
        fontSize: 1.25}
        },
  setup() {
    const art: any = ref({});
    const route = useRoute();
    const { id } = route.params;
    axios.get(`https://cms.resurgentindia.org/ghost/api/v3/content/posts/${id}?key=17e77de2cd693395fa6f1ecdb9`).then(res => {
        art.value = res.data.posts[0]
    });
    const ionRouter = useIonRouter();
    return { art, ionRouter,  personCircle, search };
  }
}
</script>
<style scoped>
div.article-body{
    font-family:Georgia, 'Times New Roman', Times, serif;
    text-align: justify;
    line-height: 1.5;
}
</style>