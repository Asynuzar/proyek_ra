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
  IonRefresher,
  IonRefresherContent,
} from "@ionic/vue";
import { defineComponent } from "vue";

import { useBackButton, useIonRouter } from "@ionic/vue";
import { App } from "@capacitor/app";

const ionRouter = useIonRouter();
useBackButton(-1, () => {
  if (!ionRouter.canGoBack()) {
    App.exitApp();
  }
});

import { reactive, onBeforeMount } from "vue";

const infoIkhtisar = reactive({ data: {} });

async function fetchIkhtisar(url) {
  const resp = await fetch(url);
  console.log(resp);
  const json = await resp.json();
  console.log(json);
  return json;
}

onBeforeMount(async () => {
  infoIkhtisar.data = await fetchIkhtisar(
    "https://maritim.kalbar.bmkg.go.id/data-api/buat-json.php?function=get_ikhtisar"
  );
});

const handleRefresh = (event) => {
  setTimeout(() => {
    const infoIkhtisar = reactive({ data: {} });

    async function fetchIkhtisar(url) {
      const resp = await fetch(url);
      console.log(resp);
      const json = await resp.json();
      console.log(json);
      return json;
    }

    onBeforeMount(async () => {
      infoIkhtisar.data = await fetchIkhtisar(
        "https://maritim.kalbar.bmkg.go.id/data-api/buat-json.php?function=get_ikhtisar"
      );
    });

    // Any calls to load data go here
    event.target.complete();
  }, 2000);
  return { handleRefresh };
};
</script>
<template>
  <ion-page>
    <ion-header class="bg-cuaca-siang">
      <ion-toolbar class="bg-cuaca-siang">
        <ion-title>Ikhtisar Cuaca Harian</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-refresher slot="fixed" @ionRefresh="handleRefresh($event)">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>
      <ion-card>
        <img alt="Pontianak" src="..\assets\img\pontianak.png" />
        <ion-card-content>
          <ion-grid>
            <ion-row>
              <ion-col>
                <h1>Ikhtisar Cuaca harian</h1>
                {{ infoIkhtisar.data.ikhtisar[0].tgl }}</ion-col
              >
            </ion-row>
          </ion-grid>
          <ion-grid>
            <ion-row>
              <ion-col>
                <img
                  alt="Suhu"
                  src="..\assets\img\temp.png"
                  width="50"
                  height="50"
                />
                <h4>Suhu Udara</h4>
                <p>
                  Max : {{ infoIkhtisar.data.ikhtisar[0].tmax }} °C<br />Min :
                  {{ infoIkhtisar.data.ikhtisar[0].tmin }} °C<br />Rata² :
                  {{ infoIkhtisar.data.ikhtisar[0].tmean }} °C<br />
                </p>
              </ion-col>
              <ion-col>
                <img
                  alt="Suhu"
                  src="..\assets\img\wind.png"
                  width="50"
                  height="50"
                />
                <h4>Angin</h4>
                <p>
                  Arah terbanyak : {{ infoIkhtisar.data.ikhtisar[0].dd }}
                  <br />Kec. Max :
                  {{ infoIkhtisar.data.ikhtisar[0].ff }} knot<br />
                </p>
              </ion-col>
              <ion-col
                ><img
                  alt="Suhu"
                  src="..\assets\img\rain.png"
                  width="50"
                  height="50"
                />
                <h4>Jumlah Curah Hujan</h4>
                <p>{{ infoIkhtisar.data.ikhtisar[0].ch }} mm<br /></p>
              </ion-col>
            </ion-row>
            <ion-row>
              <ion-col>
                <img
                  alt="Suhu"
                  src="..\assets\img\rh.png"
                  width="50"
                  height="50"
                />
                <h4>Kelembapan Udara</h4>
                <p>
                  Max : {{ infoIkhtisar.data.ikhtisar[0].rhmax }} % <br />Min :
                  {{ infoIkhtisar.data.ikhtisar[0].rhmin }} % <br />Rata² :
                  {{ infoIkhtisar.data.ikhtisar[0].rhmean }} % <br />
                </p>
              </ion-col>
              <ion-col>
                <img
                  alt="Suhu"
                  src="..\assets\img\vis.png"
                  width="50"
                  height="50"
                />
                <h4>Jarak Pandang</h4>
                <p>
                  Max : {{ infoIkhtisar.data.ikhtisar[0].vvmax }} m <br />Min :
                  {{ infoIkhtisar.data.ikhtisar[0].vvmin }} m
                  <br />
                  <br />
                </p>
              </ion-col>
              <ion-col>
                <img
                  alt="Suhu"
                  src="..\assets\img\cloudy.png"
                  width="50"
                  height="50"
                />
                <h4>Hari Tanpa Hujan</h4>
                <p>
                  {{ infoIkhtisar.data.ikhtisar[0].hth }} hari <br />
                  <br />
                </p>
              </ion-col>
            </ion-row>
          </ion-grid>
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<style scoped>
ion-col {
  text-align: center;
}

ion-header,
ion-toolbar {
  --background: linear-gradient(
    125deg,
    rgba(83, 196, 255, 1) 0%,
    rgba(0, 117, 255, 1) 100%
  );
  --color: white;
}
</style>
