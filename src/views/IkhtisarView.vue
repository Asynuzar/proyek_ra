<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Cuaca</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Geolokasi</ion-title>
        </ion-toolbar>
      </ion-header>
      <div class="ion-padding" v-if="coordinates.data">
        <h3>Lokasi Anda:</h3>
        <p>Latitude: {{ coordinates.data.coords.latitude }}</p>
        <p>Longitude: {{ coordinates.data.coords.longitude }}</p>
      </div>
    </ion-content>
  </ion-page>
</template>
<script setup>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from "@ionic/vue";
import { onMounted, reactive } from "vue";
import { Geolocation } from "@capacitor/geolocation";
const coordinates = reactive({ data: null });
onMounted(async () => {
  coordinates.data = await Geolocation.getCurrentPosition();
  console.log("Lokasi Anda:", coordinates.data);
});

import { reactive, onBeforeMount } from "vue";

const cuaca = reactive({ data: {} });

async function fetchCuaca(url) {
  const resp = await fetch(url);
  console.log(resp);
  const json = await resp.json();
  console.log(json);
  return json;
}

onBeforeMount(async () => {
  cuaca.data = await fetchCuaca(
    "https://data.bmkgapp.my.id/api/cuaca/?lat="+coordinates.data.coords.latitude + "&lon="+ coordinates.data.coords.longitude
  );
});
</script>
