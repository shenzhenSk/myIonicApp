<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 2</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 2</ion-title>
        </ion-toolbar>
      </ion-header>
      <Button size="small" @click="getCode">Take Picture</Button>
      <div>{{ code }}</div>
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
import { ref } from "vue";
import "capacitor_qrcode";
import { Plugins } from "@capacitor/core";
const { QRCodePlugin } = Plugins;
const code = ref("");
const getCode = () => {};
async function openQr() {
  const code = await QRCodePlugin.getCodeQR();
  code.value = code;
}
</script>
