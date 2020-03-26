<template>
    <section class="device-info-block mxw1200" id="infoblock">
        <v-container>
            <v-row class="height100">
                <v-col sm="12" md="6">
                    <div class="describeBlock">
                        <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
                        <p class="py-2 secondaryColor">{{textSection_1}}</p>
                    </div>
                    <div class="advantagesBlock">

                            <v-row>
                            <!--<v-col v-for="(item, i) in advantages" :key="`advantageItem${i}`" :class="`advantageItem ch grid${item.id}`">-->
                                <!--<span class="describe">{{item.describe}}</span>-->
                            <!--</v-col>-->
                                    <v-card style="width: 50%"><v-col>Стабильная доходность</v-col> </v-card>
                                    <v-card style="width: 50%"><v-col>Стабильная доходность</v-col> </v-card>
                                    <v-card style="width: 50%"><v-col>Стабильная доходность</v-col> </v-card>
                                    <v-card style="width: 50%"><v-col>Стабильная доходность</v-col> </v-card>
                                    <v-card style="width: 50%"><v-col>Стабильная доходность</v-col> </v-card>
                                    <v-card style="width: 50%"><v-col>Стабильная доходность</v-col> </v-card>
                            </v-row>

                    </div>
                </v-col>
                <container>
                    <v-row>
                 <div class="slider">
                               <div class="but1 bgbutton1" tabindex="1"></div>
                               <div class="but2 bgbutton2" tabindex="1"></div>
                               <div class="but3 bgbutton3" tabindex="1"></div>
                               <div class="img1" >
                                   <img src="img/node_1.jpg"/>
                               </div>
                               <div class="img2" >
                                   <img src="img/node_2.jpg"/>
                               </div>
                               <div class="img3">
                                   <img src="img/node_3.jpg"/>
                               </div>
                           </div>
                    </v-row>
                </container>
            </v-row>
        </v-container>
    </section>
</template>


<script>
export default {
  name: 'ProjectInfoBlock',
  data(){
      return {
            headSection: `Преимущества ACRYL Node`,
            textSection_1: `ACRYL Node – экономичен и нуждается в потреблении энергии, сравнимом с обычной лампочкой. 
                            Никаких сложных действий, простые шаги для того, чтобы начать зарабатывать. Текущая доходность от $150 в месяц. `,
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
@import "../assets/styles/slider.scss";
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
                margin-left: auto;
                margin-right: auto;
                margin-bottom: 5%;
                margin-top: 5%;
            }
        }
    }
.advantageItem:hover {
        background-color: #fedd0e;
    }

.bgbutton1 {
      background-image: url(/img/node_1.jpg);
      background-repeat: no-repeat;
      background-size: contain;
          }
.bgbutton2 {
      background-image: url(/img/node_2.jpg);
      background-repeat: no-repeat;
      background-size: contain;
          }

.bgbutton3 {
        background-image: url(/img/node_3.jpg);
        background-repeat: no-repeat;
        background-size: contain;
            }
}
</style>