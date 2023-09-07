<script setup>
const props = defineProps(["dataInfo1"]);
</script>
<template>
  <ion-card>
    <ion-card-header>
      <ion-card-title>Card Title</ion-card-title>
      <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
    </ion-card-header>

    <ion-card-content>
      <h6><b>Perairan Pati - Rembang</b></h6>
      <br />Gelombang = {{ dataInfo1.data[0].wave_desc }} <br />Kecepatan =
      {{ dataInfo1.data[0].wind_speed_min }} -
      {{ dataInfo1.data[0].wind_speed_max }} Knot <br />Arah =
      {{ dataInfo1.data[0].wind_from }} -
      {{ dataInfo1.data[0].wind_to }}
    </ion-card-content>
  </ion-card>
</template>

<style lang=""></style>
