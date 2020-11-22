<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <img src="http://new.resurgentindia.org/wp-content/uploads/2014/05/resurgentindia-copy11.png" />
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true" class="ion-padding">
      <FeaturedArticles />
      <Highlights />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonContent } from '@ionic/vue';
//import ExploreContainer from '@/components/ExploreContainer.vue';
import FeaturedArticles from '@/components/FeaturedArticles.vue';
import Highlights from '@/components/Highlights.vue';

export default  {
  name: 'Home',
  components: { FeaturedArticles, Highlights, IonHeader, IonToolbar, IonContent, IonPage }
}
</script>