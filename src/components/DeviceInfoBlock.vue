<template>
    <section class="device-info-block mxw1200">
        <v-container>
            <v-row class="height100">
                <v-col cols="12" sm="5">
                    <div class="nodeImage"></div>
                </v-col>
                <v-col cols="12" sm="7">
                    <div class="describeBlock">
                        <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
                        <p class="py-2 secondaryColor">{{textSection_1}}</p>
                    </div>
                    <div class="advantagesBlock">
                        <v-row>
                            <v-col v-for="(item, i) in advantages" :key="`advantageItem${i}`" :class="`advantageItem grid${item.id}`" cols="12" md="6">

                                <picture>
                                    <source :srcset="`/img/icon_web/${item.icon}.webp`" type="image/webp">
                                    <source :srcset="`/img/icon_web/${item.icon}.png`" type="image/png"> 
                                    <img class="icon" :src="`/img/icon_web/${item.icon}.webp`" :alt="`${item.icon}`">
                                </picture>

                                <span class="describe">{{item.describe}}</span>
                            </v-col>
                        </v-row>
                    </div>
                    <div class="py-5"><v-btn rounded color="primary secondaryColor"  href="#targetOffer" @click="Click_order2()">Заказать</v-btn></div>
                </v-col>
            </v-row>
        </v-container>
    </section>
</template>

<script>
export default {
  name: 'ProjectInfoBlock',
  data(){
      return {
            headSection: `Описание устройства`,
            textSection_1: `ACRYL Node – экономичен и нуждается в потреблении энергии, сравнимом с обычной лампочкой. 
                            Никаких сложных действий, простые шаги для того, чтобы начать зарабатывать. Текущая доходность ~ $140 в месяц. `,
            advantages: [
                {id: 1, icon: "icon_dollar", describe: "Стабильная доходность" },
                {id: 2, icon: "icon_garant", describe: "Гарантия"},
                {id: 3, icon: "icon_60wt", describe: "Компактность и бесшумность"},
                {id: 4, icon: "icon_gear", describe: "Простая установка и обслуживание"},
                {id: 5, icon: "icon_node", describe: "Малое энергопотребление"},
                {id: 6, icon: "icon_mobile", describe: "Удобное приложение"}
            ]
      }
  },
  methods: {
    Click_order2(){
      console.log("CLICK_ORDER")
      window.gaSendButton("Click_order2");
      window.yaSendButton("Click_order2");
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/index.scss";
.device-info-block{
    width: 100%;
    display: flex;
    padding: 20px 10px;
    .nodeImage{
        background-image: url(/img/NodeImg.png);
        width: 100%;
        min-height: 250px;
        @include respond-to(medium-screens) { 
            max-height: 500px;
            min-height: 500px;
        }
        height: 100%;
        background-position: top center;
        background-repeat: no-repeat;
        background-size: contain; 
    }
    .advantagesBlock{
        .advantageItem{
            display: flex;
            img.icon{
                width: 60px;
                height: 41px;
                @include respond-to(medium-screens) { 
                    width: 120px;
                    height: 80px;
                }
                @include respond-to(large-screens) { 
                    width: 75px;
                    height: 48px;
                }
                @include respond-to(wide-screens) { 
                    width: 120px;
                    height: 80px;
                }
            }
            .describe{
                padding-left: 20px;
                max-width: 170px;
            }
        }
    }
}
.height100{
    height: 100%;
}
</style>