<script setup>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonCard,
  IonCardContent,
  IonGrid,
  IonRow,
  IonCol,
} from "@ionic/vue";

import Ikhtisar from "../components/Ikhtisar.vue";
import { reactive, onBeforeMount } from "vue";

const infoIkhtisar = reactive({ data: {} });

async function fetchIkhtisar(url) {
  const resp = await fetch(url);

  const json = await resp.json();
  return json;
}

onBeforeMount(async () => {
  infoIkhtisar.data = await fetchIkhtisar(
    "https://maritim.kalbar.bmkg.go.id/data-api/buat-json.php?function=get_ikhtisar"
  );
  infoIkhtisar.data = infoIkhtisar.data.ikhtisar;
});
</script>
<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Ikhtisar Cuaca</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <Ikhtisar :InfoIkhtisar="infoIkhtisar.data" />
    </ion-content>
  </ion-page>
</template>

<style scoped>
ion-col {
  background-color: #135d54;
  border: solid 1px #fff;
  color: #fff;
  text-align: center;
}
</style>
