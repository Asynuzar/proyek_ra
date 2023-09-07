<script setup>
import { IonCard, IonCardContent, IonGrid, IonRow, IonCol } from "@ionic/vue";

const props = defineProps(["InfoIkhtisar"]);
</script>

<template>
  <ion-card>
    <img alt="Pontianak" src="..\assets\img\pontianak.jpg" />
    <ion-card-content>
      <ion-grid>
        <ion-row>
          <ion-col>
            <h3>Ikhtisar Cuaca harian</h3>
            {{ InfoIkhtisar.ikhtisar[tgl] }}</ion-col
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
              Max : {{ InfoIkhtisar.ikhtisar[0].tmax }} °C<br />Min :
              {{ InfoIkhtisar.ikhtisar[0].tmin }} °C<br />Rata-Rata :
              {{ InfoIkhtisar.ikhtisar[0].tmean }} °C<br />
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
              Arah terbanyak : {{ InfoIkhtisar.ikhtisar[0].dd }} <br />Kec. Max
              : {{ InfoIkhtisar.ikhtisar[0].ff }} knot<br />
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
            <p>{{ InfoIkhtisar.ikhtisar[0].ch }} mm<br /></p>
          </ion-col>
        </ion-row>
        <ion-row>
          <ion-col>
            <img alt="Suhu" src="..\assets\img\rh.png" width="50" height="50" />
            <h4>Kelembapan Udara</h4>
            <p>
              Max : {{ InfoIkhtisar.ikhtisar[0].rhmax }} % <br />Min :
              {{ InfoIkhtisar.ikhtisar[0].rhmin }} % <br />Rata-Rata :
              {{ InfoIkhtisar.ikhtisar[0].rhmean }} % <br />
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
              Max : {{ InfoIkhtisar.ikhtisar[0].vvmax }} m <br />Min :
              {{ InfoIkhtisar.ikhtisar[0].vvmin }} m
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
              {{ InfoIkhtisar.ikhtisar[0].hth }} hari <br />
              <br />
            </p>
          </ion-col>
        </ion-row>
      </ion-grid>
    </ion-card-content>
  </ion-card>
</template>
<style scoped>
ion-col {
  background-color: #135d54;
  color: #fff;
  text-align: center;
}
</style>
