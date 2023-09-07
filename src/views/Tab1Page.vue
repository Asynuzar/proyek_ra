<script setup>
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonCard,
  IonGrid,
  IonRow,
  IonCol,
} from "@ionic/vue";
import Gempa from "../components/Gempa.vue";
//import Pelayanan from "../components/Pelayanan.vue";
import { reactive, onBeforeMount } from "vue";

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";

import { useBackButton, useIonRouter } from "@ionic/vue";
import { App } from "@capacitor/app";

const ionRouter = useIonRouter();
useBackButton(-1, () => {
  if (!ionRouter.canGoBack()) {
    App.exitApp();
  }
});

const onSwiper = (swiper) => {
  console.log(swiper);
};
const onSlideChange = () => {
  console.log("slide change");
};

//info cuaca pelayanan
const dataInfo1 = reactive({ datad01: {} });
const dataInfo2 = reactive({ datad02: {} });
const dataInfo3 = reactive({ datad03: {} });
const dataInfo4 = reactive({ datad04: {} });
const dataInfo5 = reactive({ datad05: {} });
const dataInfo6 = reactive({ datad06: {} });
const dataInfo7 = reactive({ datad07: {} });
const dataInfo8 = reactive({ datad08: {} });
const dataInfo9 = reactive({ datad09: {} });
const dataInfo10 = reactive({ datad10: {} });
const dataInfo11 = reactive({ datad11: {} });
const dataInfo12 = reactive({ datad12: {} });
const dataInfo13 = reactive({ datad13: {} });

//info cuaca pelabuhan
const dataPel1 = reactive({ datap01: {} });
const dataPel2 = reactive({ datap02: {} });
const dataPel3 = reactive({ datap03: {} });
const dataPel4 = reactive({ datap04: {} });
const dataPel5 = reactive({ datap05: {} });
const dataPel6 = reactive({ datap06: {} });
const dataPel7 = reactive({ datap07: {} });
const dataPel8 = reactive({ datap08: {} });
const dataPel9 = reactive({ datap09: {} });
const dataPel10 = reactive({ datap10: {} });
const dataPel11 = reactive({ datap11: {} });
const dataPel12 = reactive({ datap12: {} });
const dataPel13 = reactive({ datap13: {} });
const dataPel14 = reactive({ datap14: {} });
const dataPel15 = reactive({ datap15: {} });
const dataPel16 = reactive({ datap16: {} });
const dataPel17 = reactive({ datap17: {} });
const dataPel18 = reactive({ datap18: {} });
const dataPel19 = reactive({ datap19: {} });

const infoGempa = reactive({ data: {} });
const apiGempa = "https://training20.devbmkg.my.id/gempa-terbaru";

//url peta pelayanan
const apid01 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.01_Laut%20Natuna%20Utara.json";
const apid02 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.02_Perairan%20selatan%20Kep.%20Anambas.json";
const apid03 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.03_Perairan%20utara%20Kep.%20Anambas.json";
const apid04 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.04_Perairan%20barat%20Kep.%20Natuna.json";
const apid05 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.05_Perairan%20utara%20Kep.%20Natuna.json";
const apid06 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.06_Perairan%20selatan%20Kep.%20Natuna%20-%20Pulau%20Midai.json";
const apid07 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.07_Perairan%20Kep.%20Subi%20-%20Serasan.json";
const apid08 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.08_Laut%20Natuna.json";
const apid09 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.09_Perairan%20Singkawang%20-%20Sambas.json";
const apid10 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.10_Perairan%20Pontianak%20-%20Mempawah.json";
const apid11 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.11_Perairan%20Ketapang.json";
const apid12 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.12_Perairan%20Kendawangan.json";
const apid13 =
  "https://peta-maritim.bmkg.go.id/public_api/perairan/D.13_Perairan%20Kepulauan%20Karimata.json";

//url pelabuhan
const pel01 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0009_Dwikora.json";
const pel02 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0309_PPN%20Pemangkat.json";
const pel03 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0085_Tarempa.json";
const pel04 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0088_Sintete.json";
const pel05 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0089_Sukabangun.json";
const pel06 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0310_PPP%20Sungai%20Rengas.json";
const pel07 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0311_PPP%20Teluk%20Batang.json";
const pel08 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0389_Tebas%20Kuala.json";
const pel09 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0469_Penagi.json";
const pel10 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0471_Letung.json";
const pel11 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0472_Kuala%20Maras.json";
const pel12 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0473_Pulau%20Laut.json";
const pel13 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0474_Sedanau.json";
const pel14 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0475_Pulau%20Tiga.json";
const pel15 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0476_Midai.json";
const pel16 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0477_Subi.json";
const pel17 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0478_Serasan.json";
const pel18 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0479_Rasau%20Jay.json";
const pel19 =
  "https://peta-maritim.bmkg.go.id/public_api/pelabuhan/0529_Padang%20Tikar.json";

async function fetchGempa(url) {
  const response = await fetch(url);
  const gempa = await response.json();
  infoGempa.data = gempa;
} //Fungsi fetchGempa melakukan fetch data gempa dari url

async function fetchData(url) {
  const resp = await fetch(url);
  console.log(resp);
  const json = await resp.json();
  console.log(json);
  return json;
}

onBeforeMount(async () => {
  await fetchGempa(apiGempa);
  //pelayanan
  dataInfo1.datad01 = await fetchData(apid01);
  dataInfo2.datad02 = await fetchData(apid02);
  dataInfo3.datad03 = await fetchData(apid03);
  dataInfo4.datad04 = await fetchData(apid04);
  dataInfo5.datad05 = await fetchData(apid05);
  dataInfo6.datad06 = await fetchData(apid06);
  dataInfo7.datad07 = await fetchData(apid07);
  dataInfo8.datad08 = await fetchData(apid08);
  dataInfo9.datad09 = await fetchData(apid09);
  dataInfo10.datad10 = await fetchData(apid10);
  dataInfo11.datad11 = await fetchData(apid11);
  dataInfo12.datad12 = await fetchData(apid12);
  dataInfo13.datad13 = await fetchData(apid13);
  //pelabuhan
  dataPel1.datap01 = await fetchData(pel01);
  dataPel2.datap02 = await fetchData(pel02);
  dataPel3.datap03 = await fetchData(pel03);
  dataPel4.datap04 = await fetchData(pel04);
  dataPel5.datap05 = await fetchData(pel05);
  dataPel6.datap06 = await fetchData(pel06);
  dataPel7.datap07 = await fetchData(pel07);
  dataPel8.datap08 = await fetchData(pel08);
  dataPel9.datap09 = await fetchData(pel09);
  dataPel10.datap10 = await fetchData(pel10);
  dataPel11.datap11 = await fetchData(pel11);
  dataPel12.datap12 = await fetchData(pel12);
  dataPel13.datap13 = await fetchData(pel13);
  dataPel14.datap14 = await fetchData(pel14);
  dataPel15.datap15 = await fetchData(pel15);
  dataPel16.datap16 = await fetchData(pel16);
  dataPel17.datap17 = await fetchData(pel17);
  dataPel18.datap18 = await fetchData(pel18);
  dataPel19.datap19 = await fetchData(pel19);
});
</script>

<template>
  <ion-page>
    <ion-header class="bg-cuaca-siang">
      <ion-toolbar>
        <ion-title>Beranda</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <div class="p-2">
        <h4><b>Prakiraan Cuaca Wilayah Pelayanan</b></h4>
      </div>
      <swiper
        :slides-per-view="1.5"
        :space-between="2"
        @swiper="onSwiper"
        @slideChange="onSlideChange"
      >
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo1.datad01.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo1.datad01.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo1.datad01.data[0].weather }}<br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo1.datad01.data[0].wind_from }} -
              {{ dataInfo1.datad01.data[0].wind_to }}<br />
              {{ dataInfo1.datad01.data[0].wind_speed_min }} -
              {{ dataInfo1.datad01.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo1.datad01.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo2.datad02.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo2.datad02.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo2.datad02.data[0].weather }}<br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo2.datad02.data[0].wind_from }} -
              {{ dataInfo2.datad02.data[0].wind_to }}<br />
              {{ dataInfo2.datad02.data[0].wind_speed_min }} -
              {{ dataInfo2.datad02.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo2.datad02.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo3.datad03.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo3.datad03.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo3.datad03.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo3.datad03.data[0].wind_from }} -
              {{ dataInfo3.datad03.data[0].wind_to }}<br />
              {{ dataInfo3.datad03.data[0].wind_speed_min }} -
              {{ dataInfo3.datad03.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo3.datad03.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo4.datad04.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo4.datad04.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo4.datad04.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo4.datad04.data[0].wind_from }} -
              {{ dataInfo4.datad04.data[0].wind_to }}<br />
              {{ dataInfo4.datad04.data[0].wind_speed_min }} -
              {{ dataInfo4.datad04.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo4.datad04.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo5.datad05.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo5.datad05.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo5.datad05.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo5.datad05.data[0].wind_from }} -
              {{ dataInfo5.datad05.data[0].wind_to }}<br />
              {{ dataInfo5.datad05.data[0].wind_speed_min }} -
              {{ dataInfo5.datad05.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo5.datad05.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo6.datad06.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo6.datad06.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo6.datad06.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo6.datad06.data[0].wind_from }} -
              {{ dataInfo6.datad06.data[0].wind_to }}<br />
              {{ dataInfo6.datad06.data[0].wind_speed_min }} -
              {{ dataInfo6.datad06.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo6.datad06.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo7.datad07.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo7.datad07.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo7.datad07.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo7.datad07.data[0].wind_from }} -
              {{ dataInfo7.datad07.data[0].wind_to }}<br />
              {{ dataInfo7.datad07.data[0].wind_speed_min }} -
              {{ dataInfo7.datad07.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo7.datad07.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo8.datad08.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo8.datad08.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo8.datad08.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo8.datad08.data[0].wind_from }} -
              {{ dataInfo8.datad08.data[0].wind_to }}<br />
              {{ dataInfo8.datad08.data[0].wind_speed_min }} -
              {{ dataInfo8.datad08.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo8.datad08.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo9.datad09.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo9.datad09.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo9.datad09.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo9.datad09.data[0].wind_from }} -
              {{ dataInfo9.datad09.data[0].wind_to }}<br />
              {{ dataInfo9.datad09.data[0].wind_speed_min }} -
              {{ dataInfo9.datad09.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo9.datad09.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo10.datad10.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo10.datad10.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo10.datad10.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo10.datad10.data[0].wind_from }} -
              {{ dataInfo10.datad10.data[0].wind_to }}<br />
              {{ dataInfo10.datad10.data[0].wind_speed_min }} -
              {{ dataInfo10.datad10.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo10.datad10.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo11.datad11.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo11.datad11.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo11.datad11.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo11.datad11.data[0].wind_from }} -
              {{ dataInfo11.datad11.data[0].wind_to }}<br />
              {{ dataInfo11.datad11.data[0].wind_speed_min }} -
              {{ dataInfo11.datad11.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo11.datad11.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo12.datad12.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo12.datad12.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo12.datad12.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo12.datad12.data[0].wind_from }} -
              {{ dataInfo12.datad12.data[0].wind_to }}<br />
              {{ dataInfo12.datad12.data[0].wind_speed_min }} -
              {{ dataInfo12.datad12.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo12.datad12.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelayanan">
            <ion-card-header>
              <ion-card-subtitle>
                {{ dataInfo13.datad13.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataInfo13.datad13.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <br />
              {{ dataInfo13.datad13.data[0].weather }} <br />
              <img
                alt="Angin"
                src="..\assets\img\wind.svg"
                width="20"
                height="20"
              />
              {{ dataInfo13.datad13.data[0].wind_from }} -
              {{ dataInfo13.datad13.data[0].wind_to }}<br />
              {{ dataInfo13.datad13.data[0].wind_speed_min }} -
              {{ dataInfo13.datad13.data[0].wind_speed_max }} Knot <br />
              <img
                alt="Gelombang"
                src="..\assets\img\wave.svg"
                width="20"
                height="20"
              />
              {{ dataInfo13.datad13.data[0].wave_desc }}
            </ion-card-content>
          </ion-card>
        </swiper-slide>
      </swiper>

      <br />

      <Gempa :infoGempa="infoGempa.data" />
      <!--  :infoGempa="infoGempa.data" adalah props yang dikirim ke komponen Gempa.vue
          nama variabelnya adalah infoGempa, variabel yang dikirim adalah infoGempa.data
    -->
      <div class="p-2">
        <h4><b>Prakiraan Cuaca Pelabuhan</b></h4>
      </div>
      <swiper
        :slides-per-view="2.2"
        :space-between="2"
        @swiper="onSwiper"
        @slideChange="onSlideChange"
      >
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel1.datap01.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel1.datap01.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel1.datap01.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel1.datap01.data[0].wind_from }} -
                  {{ dataPel1.datap01.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel1.datap01.data[0].wind_speed_min }} -
                  {{ dataPel1.datap01.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel1.datap01.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel2.datap02.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel2.datap02.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel2.datap02.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel2.datap02.data[0].wind_from }} -
                  {{ dataPel2.datap02.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel2.datap02.data[0].wind_speed_min }} -
                  {{ dataPel2.datap02.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel2.datap02.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel3.datap03.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel3.datap03.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel3.datap03.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel3.datap03.data[0].wind_from }} -
                  {{ dataPel3.datap03.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel3.datap03.data[0].wind_speed_min }} -
                  {{ dataPel3.datap03.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel3.datap03.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel4.datap04.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel4.datap04.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel4.datap04.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel4.datap04.data[0].wind_from }} -
                  {{ dataPel4.datap04.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel4.datap04.data[0].wind_speed_min }} -
                  {{ dataPel4.datap04.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel4.datap04.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel5.datap05.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel5.datap05.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel5.datap05.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel5.datap05.data[0].wind_from }} -
                  {{ dataPel5.datap05.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel5.datap05.data[0].wind_speed_min }} -
                  {{ dataPel5.datap05.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel5.datap05.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel6.datap06.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel6.datap06.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel6.datap06.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel6.datap06.data[0].wind_from }} -
                  {{ dataPel6.datap06.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel6.datap06.data[0].wind_speed_min }} -
                  {{ dataPel6.datap06.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel6.datap06.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel7.datap07.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel7.datap07.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel7.datap07.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel7.datap07.data[0].wind_from }} -
                  {{ dataPel7.datap07.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel7.datap07.data[0].wind_speed_min }} -
                  {{ dataPel7.datap07.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel7.datap07.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel8.datap08.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel8.datap08.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel8.datap08.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel8.datap08.data[0].wind_from }} -
                  {{ dataPel8.datap08.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel8.datap08.data[0].wind_speed_min }} -
                  {{ dataPel8.datap08.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel8.datap08.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel9.datap09.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel9.datap09.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel9.datap09.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel9.datap09.data[0].wind_from }} -
                  {{ dataPel9.datap09.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel9.datap09.data[0].wind_speed_min }} -
                  {{ dataPel9.datap09.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel9.datap09.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel10.datap10.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel10.datap10.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel10.datap10.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel10.datap10.data[0].wind_from }} -
                  {{ dataPel10.datap10.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel10.datap10.data[0].wind_speed_min }} -
                  {{ dataPel10.datap10.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel10.datap10.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel11.datap11.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel11.datap11.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel11.datap11.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel11.datap11.data[0].wind_from }} -
                  {{ dataPel11.datap11.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel11.datap11.data[0].wind_speed_min }} -
                  {{ dataPel11.datap11.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel11.datap11.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel12.datap12.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel12.datap12.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel12.datap12.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel12.datap12.data[0].wind_from }} -
                  {{ dataPel12.datap12.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel12.datap12.data[0].wind_speed_min }} -
                  {{ dataPel12.datap12.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel12.datap12.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel13.datap13.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel13.datap13.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel13.datap13.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel13.datap13.data[0].wind_from }} -
                  {{ dataPel13.datap13.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel13.datap13.data[0].wind_speed_min }} -
                  {{ dataPel13.datap13.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel13.datap13.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel14.datap14.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel14.datap14.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel14.datap14.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel14.datap14.data[0].wind_from }} -
                  {{ dataPel14.datap14.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel14.datap14.data[0].wind_speed_min }} -
                  {{ dataPel14.datap14.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel14.datap14.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel15.datap15.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel15.datap15.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel15.datap15.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel15.datap15.data[0].wind_from }} -
                  {{ dataPel15.datap15.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel15.datap15.data[0].wind_speed_min }} -
                  {{ dataPel15.datap15.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel15.datap15.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel16.datap16.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel16.datap16.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel16.datap16.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel16.datap16.data[0].wind_from }} -
                  {{ dataPel16.datap16.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel16.datap16.data[0].wind_speed_min }} -
                  {{ dataPel16.datap16.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel16.datap16.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel17.datap17.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel17.datap17.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel17.datap17.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel17.datap17.data[0].wind_from }} -
                  {{ dataPel17.datap17.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel17.datap17.data[0].wind_speed_min }} -
                  {{ dataPel17.datap17.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel17.datap17.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel18.datap18.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel18.datap18.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel18.datap18.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel18.datap18.data[0].wind_from }} -
                  {{ dataPel18.datap18.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel18.datap18.data[0].wind_speed_min }} -
                  {{ dataPel18.datap18.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel18.datap18.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
        <swiper-slide>
          <ion-card class="card-pelabuhan">
            <ion-card-header>
              <ion-card-title> Pelabuhan</ion-card-title>
              <ion-card-subtitle>
                {{ dataPel19.datap19.name }}
              </ion-card-subtitle>
            </ion-card-header>
            <ion-card-content>
              <img
                alt="Cuaca"
                :src="
                  'https://www.bmkg.go.id/asset/img/icon-cuaca/' +
                  dataPel19.datap19.data[0].weather +
                  '-am.png'
                "
                width="80"
                height="80"
              />
              <div class="pel">
                <p>{{ dataPel19.datap19.data[0].weather }}</p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Angin"
                    src="..\assets\img\wind.svg"
                    width="20"
                    height="20"
                  />

                  {{ dataPel19.datap19.data[0].wind_from }} -
                  {{ dataPel19.datap19.data[0].wind_to }}
                </p>
              </div>
              <div class="pel">
                <p>
                  {{ dataPel19.datap19.data[0].wind_speed_min }} -
                  {{ dataPel19.datap19.data[0].wind_speed_max }} Knot
                </p>
              </div>
              <div class="pel">
                <p>
                  <img
                    alt="Gelombang"
                    src="..\assets\img\wave.svg"
                    width="20"
                    height="20"
                  />
                  {{ dataPel19.datap19.data[0].wave_desc }}
                </p>
              </div>
            </ion-card-content>
          </ion-card>
        </swiper-slide>
      </swiper>
    </ion-content>
  </ion-page>
</template>

<style scoped>
ion-card-title,
ion-card-subtitle,
ion-card-content,
ion-card-header {
  text-align: center;
  color: black;
}

div.pel {
  background: rgba(234, 241, 234, 0.5);
}

.card-pelayanan {
  background-image: url("..\assets\img\laut.png"); /* The image used */
  background-color: #66b1d3; /* Used if the image is unavailable */
  height: 250px; /* You must set a specified height */
  background-position: center; /* Center the image */
  background-repeat: no-repeat; /* Do not repeat the image */
  background-size: cover; /* Resize the background image to cover the entire container */
}

.card-pelabuhan {
  background-image: url("..\assets\img\pelabuhan2.jpg"); /* The image used */
  background-color: #66b1d3; /* Used if the image is unavailable */
  height: 300px; /* You must set a specified height */
  background-position: center; /* Center the image */
  background-repeat: no-repeat; /* Do not repeat the image */
  background-size: cover; /* Resize the background image to cover the entire container */
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
