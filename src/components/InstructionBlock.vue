<template>
    <section class="instruction-block mxw1200v2">
        <v-container>
            <v-row class="height100">
                <v-col cols="12" sm="12">
                    <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
                    <v-timeline align-top dense>
                        <v-timeline-item 
                            v-for="(step, i) in steps" 
                            :key="`step${i}`"
                            icon="mdi-check">
                            <v-card class="elevation-2">
                                <v-card-text>{{step.text}}</v-card-text>
                            </v-card>
                        </v-timeline-item>
                    </v-timeline>
                </v-col>
            </v-row>
        </v-container>
    </section>
</template>

<script>
export default {
  name: 'InstructionBlock',
  props: ['addressItems'],
  data(){
      return {
            headSection: `Инструкция по использованию`,
            steps: [
                {id: 1, text: `Заказываете ACRYL Node`},
                {id: 2, text: `Подключаете ACRYL Node к сети и питанию`},
                {id: 3, text: `Устанавливаете приложение ACRYL Client (AppStore / GooglePlay)`},
                {id: 4, text: `Оставляете монеты на балансе для большей доходности`},
                {id: 5, text: `Обмениваете монеты на биткоины и выводите в фиат`}
            ]
      }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/index.scss";
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
</style>