<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>First Tab</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <FeaturedArticles />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
//import ExploreContainer from '@/components/ExploreContainer.vue';
import FeaturedArticles from '@/components/FeaturedArticles.vue';

export default  {
  name: 'Tab1',
  components: { FeaturedArticles, IonHeader, IonToolbar, IonTitle, IonContent, IonPage }
}
</script>