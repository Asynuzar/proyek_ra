<script setup>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonCardContent,
  IonCardHeader,
  IonCardTitle,
  IonCardSubtitle,
  IonAccordion,
  IonAccordionGroup,
  IonItem,
  IonLabel,
  IonRefresher,
  IonRefresherContent,
} from "@ionic/vue";

import { useBackButton, useIonRouter } from "@ionic/vue";
import { App } from "@capacitor/app";

const ionRouter = useIonRouter();
useBackButton(-1, () => {
  if (!ionRouter.canGoBack()) {
    App.exitApp();
  }
});

import { reactive, onBeforeMount } from "vue";

const infoWisata = reactive({ data: {} });

async function fetchWisata(url) {
  const resp = await fetch(url);
  console.log(resp);
  const json = await resp.json();
  console.log(json);
  return json;
}

onBeforeMount(async () => {
  infoWisata.data = await fetchWisata(
    "https://maritim.kalbar.bmkg.go.id/data-api/buat-json.php?function=get_wisata"
  );
});

const handleRefresh = (event) => {
  setTimeout(() => {
    const infoWisata = reactive({ data: {} });

    async function fetchWisata(url) {
      const resp = await fetch(url);
      console.log(resp);
      const json = await resp.json();
      console.log(json);
      return json;
    }

    onBeforeMount(async () => {
      infoWisata.data = await fetchWisata(
        "https://maritim.kalbar.bmkg.go.id/data-api/buat-json.php?function=get_wisata"
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
    <ion-header>
      <ion-toolbar class="bg-cuaca-siang">
        <ion-title>Prakiraan Cuaca Wisata Bahari</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-refresher slot="fixed" @ionRefresh="handleRefresh($event)">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>
      <ion-card>
        <img alt="lemukutan" src="..\assets\img\lemukutan.png" />
        <ion-card-header>
          <ion-card-title>Pulau Lemukutan</ion-card-title>
          <ion-card-subtitle>{{
            infoWisata.data.pelabuhan[0].tanggal
          }}</ion-card-subtitle>
        </ion-card-header>

        <ion-card-content>
          <ion-accordion-group>
            <ion-accordion value="first">
              <ion-item slot="header" color="light">
                <ion-label>Pelabuhan Teluk Suak</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.pelabuhan[1].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.pelabuhan[1].cuaca }}</ion-label
                    >
                  </ion-item>

                  <ion-item>
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Maks"
                        src="..\assets\img\high-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label
                      >{{
                        parseFloat(infoWisata.data.pelabuhan[1]["pasut_maks"])
                      }}
                      m | Jam :{{
                        infoWisata.data.pelabuhan[1].waktu_maks
                      }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Pasut Min"
                        src="..\assets\img\low-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{
                        parseFloat(infoWisata.data.pelabuhan[1]["pasut_min"])
                      }}
                      m | Jam :
                      {{ infoWisata.data.pelabuhan[1].waktu_min }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
            <ion-accordion value="second">
              <ion-item slot="header" color="light">
                <ion-label>Rute Penyebrangan</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.penyebrangan[2].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[2].cuaca }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Angin"
                        src="..\assets\img\wind.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{
                        infoWisata.data.penyebrangan[2].arah_angin
                      }}</ion-label
                    >
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[2].kec_angin }}
                      knot</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Arus"
                        src="..\assets\img\current.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[2].arah_arus }}
                    </ion-label>
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[2].kec_arus }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Gelombang"
                        src="..\assets\img\wave.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[2].gelombang }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
            <ion-accordion value="third">
              <ion-item slot="header" color="light">
                <ion-label>Pulau Lemukutan</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.wisata[2].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>{{ infoWisata.data.wisata[2].cuaca }}</ion-label>
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Angin"
                        src="..\assets\img\wind.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.wisata[2].arah_angin }}</ion-label
                    >
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.wisata[2].kec_angin }}
                      knot
                    </ion-label>
                  </ion-item>
                  <ion-item>
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Maks"
                        src="..\assets\img\high-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label
                      >{{ parseFloat(infoWisata.data.wisata[2]["pasut_maks"]) }}
                      m | Jam :
                      {{ infoWisata.data.wisata[2].waktu_maks }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Min"
                        src="..\assets\img\low-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label
                      >{{ parseFloat(infoWisata.data.wisata[2]["pasut_min"]) }}
                      m | Jam :
                      {{ infoWisata.data.wisata[2].waktu_min }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Gelombang"
                        src="..\assets\img\wave.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label
                      >Gelombang :
                      {{ infoWisata.data.wisata[2].gelombang }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
          </ion-accordion-group>
        </ion-card-content>
      </ion-card>
      <ion-card>
        <img alt="temajo" src="..\assets\img\temajo.png" />
        <ion-card-header>
          <ion-card-title>Pulau Temajo</ion-card-title>
          <ion-card-subtitle>{{
            infoWisata.data.pelabuhan[0].tanggal
          }}</ion-card-subtitle>
        </ion-card-header>

        <ion-card-content>
          <ion-accordion-group>
            <ion-accordion value="first">
              <ion-item slot="header" color="light">
                <ion-label>Pelabuhan Sui. Kunyit</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.pelabuhan[0].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.pelabuhan[0].cuaca }}</ion-label
                    >
                  </ion-item>

                  <ion-item>
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Maks"
                        src="..\assets\img\high-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{
                        parseFloat(infoWisata.data.pelabuhan[0]["pasut_maks"])
                      }}
                      m | Jam :
                      {{ infoWisata.data.pelabuhan[0].waktu_maks }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Pasut Min"
                        src="..\assets\img\low-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{
                        parseFloat(infoWisata.data.pelabuhan[0]["pasut_min"])
                      }}
                      m | Jam :
                      {{ infoWisata.data.pelabuhan[0].waktu_min }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
            <ion-accordion value="second">
              <ion-item slot="header" color="light">
                <ion-label>Rute Penyebrangan</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.penyebrangan[1].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[1].cuaca }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Angin"
                        src="..\assets\img\wind.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{
                        infoWisata.data.penyebrangan[1].arah_angin
                      }}</ion-label
                    >
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[1].kec_angin }}
                      knot</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Arus"
                        src="..\assets\img\current.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[1].arah_arus }}
                    </ion-label>
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[1].kec_arus }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Gelombang"
                        src="..\assets\img\wave.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[1].gelombang }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
            <ion-accordion value="third">
              <ion-item slot="header" color="light">
                <ion-label>Pulau Temajo</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.wisata[1].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.wisata[1].cuaca }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Angin"
                        src="..\assets\img\wind.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.wisata[1].arah_angin }}</ion-label
                    >
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.wisata[1].kec_angin }}
                      knot
                    </ion-label>
                  </ion-item>
                  <ion-item>
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Maks"
                        src="..\assets\img\high-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ parseFloat(infoWisata.data.wisata[1]["pasut_maks"]) }}
                      m | Jam :
                      {{ infoWisata.data.wisata[1].waktu_maks }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Min"
                        src="..\assets\img\low-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label
                      >{{ parseFloat(infoWisata.data.wisata[1]["pasut_min"]) }}
                      m | Jam :
                      {{ infoWisata.data.wisata[1].waktu_min }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Gelombang"
                        src="..\assets\img\wave.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.wisata[1].gelombang }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
          </ion-accordion-group>
        </ion-card-content>
      </ion-card>
      <ion-card>
        <img alt="karimata" src="..\assets\img\karimata.png" />
        <ion-card-header>
          <ion-card-title>Pulau Karimata</ion-card-title>
          <ion-card-subtitle>{{
            infoWisata.data.pelabuhan[0].tanggal
          }}</ion-card-subtitle>
        </ion-card-header>

        <ion-card-content>
          <ion-accordion-group>
            <ion-accordion value="second">
              <ion-item slot="header" color="light">
                <ion-label>Rute Penyebrangan</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.penyebrangan[0].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[0].cuaca }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Angin"
                        src="..\assets\img\wind.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{
                        infoWisata.data.penyebrangan[0].arah_angin
                      }}</ion-label
                    >
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[0].kec_angin }}
                      knot</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Arus"
                        src="..\assets\img\current.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[0].arah_arus }}
                    </ion-label>
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[0].kec_arus }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Gelombang"
                        src="..\assets\img\wave.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.penyebrangan[0].gelombang }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
            <ion-accordion value="third">
              <ion-item slot="header" color="light">
                <ion-label>Pulau Karimata</ion-label>
              </ion-item>
              <div class="ion-padding" slot="content">
                <ion-list>
                  <ion-item>
                    <ion-thumbnail slot="start">
                      <img
                        alt="Cuaca"
                        :src="
                          'https://maritim.kalbar.bmkg.go.id/images/' +
                          infoWisata.data.wisata[0].cuaca +
                          '.png'
                        "
                        width="40"
                        height="40"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.wisata[0].cuaca }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Angin"
                        src="..\assets\img\wind.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.wisata[0].arah_angin }}</ion-label
                    >
                  </ion-item>
                  <ion-item>
                    <ion-label>
                      {{ infoWisata.data.wisata[0].kec_angin }}
                      knot
                    </ion-label>
                  </ion-item>
                  <ion-item>
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Maks"
                        src="..\assets\img\high-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ parseFloat(infoWisata.data.wisata[0]["pasut_maks"]) }}
                      m | Jam :
                      {{ infoWisata.data.wisata[0].waktu_maks }}</ion-label
                    >
                  </ion-item>

                  <ion-item lines="none">
                    <ion-thumbnail slot="end">
                      <img
                        alt="Pasut Min"
                        src="..\assets\img\low-tide.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ parseFloat(infoWisata.data.wisata[0]["pasut_min"]) }}
                      m | Jam :
                      {{ infoWisata.data.wisata[0].waktu_min }}</ion-label
                    >
                  </ion-item>
                  <ion-item lines="none">
                    <ion-thumbnail slot="start">
                      <img
                        alt="Gelombang"
                        src="..\assets\img\wave.svg"
                        width="20"
                        height="20"
                      />
                    </ion-thumbnail>
                    <ion-label>
                      {{ infoWisata.data.wisata[0].gelombang }}</ion-label
                    >
                  </ion-item>
                </ion-list>
              </div>
            </ion-accordion>
          </ion-accordion-group>
        </ion-card-content>
      </ion-card>
      <Lemukutan />
    </ion-content>
  </ion-page>
</template>

<style scoped>
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
