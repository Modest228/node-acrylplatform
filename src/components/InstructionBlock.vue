<template>
    <section class="instruction-block mxw1200v2" id="instructionblock" align="left">
            <v-container>
                <v-row class="height100">
                    <v-col cols="12" sm="12">
                        <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
            </v-col>

                    <div class="wrap">
                        <div class="slider">
                            <v-col class="elevation-1 colpos"></v-col>
                            <div class="but1" tabindex="1"><p class="t1">1</p><p  class="pedit">Заказать</p></div>
                            <div class="but2" tabindex="1"><p class="t2">2</p><p class="pedit">Подключить</p></div>
                            <div class="but3" tabindex="1"><p class="t3">3</p><p class="pedit">Установить</p></div>
                            <div class="but4" tabindex="1"><p class="t4">4</p><p class="pedit">Заработать</p></div>
                            <div class="but5" tabindex="1"><p class="t5">5</p><p class="pedit">Вывести</p></div>
                            <div class="round1 nav"></div>
                            <div class="round2 nav"></div>
                            <div class="round3 nav"></div>
                            <div class="round4 nav"></div>
                            <div class="round5 nav"></div>
                            <div class="img1 opis" >
                                <img alt="step1" class="ini" src="img/an_step_1.jpg"/>
                                <img alt="step1m" class="hii" src="img/an_step_5m.jpg"/>
                            </div>
                            <div class="img2 opis" >
                                <img alt="step2" class="ini" src="img/an_step_2.jpg"/>
                                <img alt="step2m" class="hii" src="img/an_step_2m.jpg"/>
                            </div>
                            <div class="img3 opis">
                                <img alt="step3" class="ini" src="img/an_step_3.jpg"/>
                                <img alt="step3m" class="hii" src="img/an_step_4m.jpg"/>
                            </div>
                            <div class="img4 opis">
                                <img alt="step4" class="ini" src="img/an_step_4.jpg" />
                                <img alt="step4m" class="hii" src="img/an_step_3m.jpg"/>
                            </div>
                            <div class="img5 opis">
                                <img alt="step5" class="ini" src="img/an_step_5.jpg"/>
                                <img alt="step5m" class="hii" src="img/an_step_1m.jpg"/>
                            </div>
                        </div>
                    </div>
        </v-row>
                <v-btn  class="mbtn" rounded color="bauto" href="#targetOffer" align="center" @click="Click_more()">Заказать</v-btn>
    </v-container>
  </section>
</template>

<script>
  export default {
    data: () => ({
    headSection: `Пошаговая инструкция`,
      items: [
        {
          color: '#fedd0e',
          icon: 'mdi-numeric-1',
          text: 'Заказываете ACRYL Node',
        },
        {
           color: '#fedd0e',
          icon: 'mdi-numeric-2',
          text: 'Подключаете ACRYL Node к сети и питанию',
        },
        {
          color: '#fedd0e',
          icon: 'mdi-numeric-3',
          text: 'Устанавливаете приложение ACRYL Client (AppStore / GooglePlay)',
        },
        {
          color: '#fedd0e',
          icon: 'mdi-numeric-4',
          text: 'Оставляете монеты на балансе для большей доходности',
        },
         {
          color: '#fedd0e',
          icon: 'mdi-numeric-5',
          text: 'Обмениваете монеты на биткоины и выводите в фиат',
         },
      ],
    }),
  }
</script>

<style lang="scss" scoped>
@import "../assets/styles/index.scss";
@import "../assets/styles/sliderv2.scss";
.instruction-block{
    width: 100%;
    display: flex;
    padding: 20px 10px;
    .vStepper{
        border: none;
        box-shadow: none;
    }
}
.height100{
    height: 100%;
}

.bauto {
    margin-left: 42%;
}

.theme--light.v-btn:not(.v-btn--flat):not(.v-btn--text):not(.v-btn--outlined) {
    background-color: black;
}
.theme--light.v-btn:not(.v-btn--flat):not(.v-btn--text):not(.v-btn--outlined):hover {
    background-color: #3C3C40;
}
.colpos {
    width: 100%;
    height: 50px;
    margin-top: -30px;

}
.pedit {
    margin-left: 115%;
    margin-top: -40px;
}
.hii {
    visibility: hidden;
    position: absolute;
}
.wrap {
 max-width: 1280px;
}
.mbtn {
    margin-top: -1%;
}
@media (max-width: 600px) {
    .pedit {
        visibility: hidden;
    }
    .bauto {
        margin-left: 36%;
    }
    .ini {
        visibility: hidden;
    }
    .hii {
        visibility: inherit;
        min-width: 800px;
        margin-left: -15%;
    }
    .mbtn {
        margin-top: 14%;
        margin-left: 31%;
    }
}
@media (max-width: 500px) {
    .hii {
        min-width: 800px;
        margin-left: -165%;
    }
}
</style>