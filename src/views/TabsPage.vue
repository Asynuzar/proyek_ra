<script setup>
import {
  IonTabBar,
  IonTabButton,
  IonTabs,
  IonLabel,
  IonIcon,
  IonPage,
  IonRouterOutlet,
} from "@ionic/vue";
import {
  homeOutline,
  cloudOutline,
  pulseOutline,
  thermometerOutline,
} from "ionicons/icons";
</script>
<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
      <ion-tab-bar class="bg-cuaca-siang" slot="bottom">
        <ion-tab-button tab="tab1" href="/tab1">
          <ion-icon aria-hidden="true" :icon="homeOutline" />

          <ion-label>Beranda</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab2" href="/tab2">
          <ion-icon aria-hidden="true" :icon="cloudOutline" />
          <ion-label>Cuaca Wisata</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab3" href="/tab3">
          <ion-icon aria-hidden="true" :icon="thermometerOutline" />
          <ion-label>Ikhtisar Cuaca</ion-label>
        </ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>
