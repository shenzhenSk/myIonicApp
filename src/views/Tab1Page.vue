<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 1</ion-title>
        </ion-toolbar>
      </ion-header>
      <Button size="small" @click="takePicture">Take Picture</Button>
      <img v-if="imageSrc" :src="imageSrc" class="" alt="" />
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from "@ionic/vue";
import ExploreContainer from "@/components/ExploreContainer.vue";
import { Camera, CameraResultType } from "@capacitor/camera";
import { ref } from "vue";
const imageSrc: any = ref("");
const takePicture = async () => {
  try {
    const image = await Camera.getPhoto({
      quality: 90,
      allowEditing: true,
      resultType: CameraResultType.Uri,
    });
    const imageUrl = image.webPath;
    imageSrc.value = imageUrl;
    console.log(imageSrc.value);
  } catch (error) {
    console.log(error);
  }
};
</script>
