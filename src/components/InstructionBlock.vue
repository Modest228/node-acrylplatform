<template>
    <section class="instruction-block mxw1200v2" id="instructionblock" align="left">
            <v-container>
                <v-row class="height100">
                    <v-col cols="12" sm="12">
                        <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
            </v-col>
                    <div class="slider">
                        <div class="but1" tabindex="1"></div>
                        <div class="but2" tabindex="1"></div>
                        <div class="but3" tabindex="1"></div>
                        <div class="but4" tabindex="1"></div>
                        <div class="but5" tabindex="1"></div>
                        <div class="img1" >
                            <img src="img/an_step_1.jpg"/>
                        </div>
                        <div class="img2" >
                            <img src="img/an_step_2.jpg"/>
                        </div>
                        <div class="img3">
                            <img src="img/an_step_3.jpg"/>
                        </div>
                        <div class="img4">
                            <img src="img/an_step_4.jpg"/>
                        </div>
                        <div class="img5">
                            <img src="img/an_step_5.jpg"/>
                        </div>
                    </div>
                    <v-btn rounded color="bbtn bauto secondaryColor" href="#targetOffer" align="center" @click="Click_more()">Заказать</v-btn>
        </v-row>
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
    margin-left: auto;
    margin-right: auto;
    margin-top: 1%;
}
</style>