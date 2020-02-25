<template>
    <section class="calc-block">
        <v-card class="calc-card">
            <v-container>
                <v-row>
                    <v-col>
                        <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
                    </v-col>
                </v-row>
                <v-row class="formNodeCount">
                    <v-col cols="12" xs="12" sm="12" md="4" class="maxWidth320 CountNodeHead px-3">
                        <label for="formNodecountNode">{{countNodeHead}}</label>
                        <input id="formNodecountNode" class="formNodeCountInput" name="countNode" type="text" :value="`${countNode}`" disabled/>
                        <v-slider
                            v-model="countNode"
                            track-color="grey"
                            always-dirty
                            min="1"
                            max="30"
                            class="formNodeCountSlider"
                        >
                        </v-slider>
                    </v-col>
                    <v-col cols="12" xs="12" sm="12" md="4" class="maxWidth320 CountMonthHead px-3">
                        <label for="formNodecountMonth">{{countMonthHead}}</label>
                        <input id="formNodecountMonth" class="formNodeCountInput" name="countMonth" type="text" :value="`${countMonth}`" disabled/>
                        <v-slider
                            v-model="countMonth"
                            track-color="grey"
                            always-dirty
                            min="1"
                            max="36"
                            class="formNodeCountSlider"
                        >
                        </v-slider>    
                    </v-col>
                    <v-col cols="12" md="4" class="maxWidth320 IncomeHead px-3">
                        <label for="formNodeincome">{{incomeHead}}</label>
                        <input id="formNodeincome" class="formNodeCountInput" name="income" type="text" :value="`$${income}`" />
                    </v-col>
                </v-row>
            </v-container>
        </v-card>
    </section>
</template>

<script>
export default {
  name: 'CalcBlock',
  data(){
      return {
            headSection: `Калькулятор доходности`,
            countNodeHead: `Кол-во ACRYL Node`,
                countNode: 1,
            countMonthHead: `Кол-во месяцев`,
                countMonth: 12,
            incomeHead: `Доход`,
            // checkBoxLabel: `Получать повышенный доход, сохраняя заработанные монеты на генерирующем балансе устройстве.`,
            // checkBoxInput: false
      }
  },
  computed: {
      income() {
            let countNode = this.countNode; //Кол-во нод
            let countMonth = this.countMonth; //Период в месяцах

            let GENERATOR_BALANCE = 800; //Генерирующий баланс на начало периода
            const COURSE_ACRYL = 13; // Курс акрила к доллору
            let INCOME_MONTH = 180/1000 * GENERATOR_BALANCE; //Доходность одной ноды в месяц

            let incomeOnMonth = INCOME_MONTH / COURSE_ACRYL; // Доходность одной ноды в месяц в акрилах
            
            const res = incomeOnMonth * countNode * countMonth * COURSE_ACRYL;
            return res.toFixed(0);
        }
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/index.scss";
.calc-block{
    .calc-card{
        margin: 20px 10px;
        border-radius: 20px !important; 
        padding-top: 30px;
        padding-bottom: 30px;
    }
    .headSection{
        text-align: center;
        width: 300px;
        margin: 0 auto 10px;
    }
    .formNodeCount{
        .maxWidth320{
            max-width: 320px;
            margin: 0 auto;
        }
        .CountNodeHead{
            text-align: center;
            width: 100%;
            label{
                padding: 10px 0;
            }
            .formNodeCountInput{
                width: 100%;
                border: 1px solid #B4C0D2;
                border-radius: 20px;
                text-align: center;
                height: 42px;
                margin-bottom: -10px;
                margin-top: 10px;
            }
            .formNodeCountSlider{
                margin-top: -9px;
                padding: 0 10px;
            }
        }
        .CountMonthHead{
            text-align: center;
            width: 100%;
            label{
                padding: 10px 0;
            }
            .formNodeCountInput{
                width: 100%;
                border: 1px solid #B4C0D2;
                border-radius: 20px;
                text-align: center;
                height: 42px;
                margin-bottom: -10px;
                margin-top: 10px;
            }
            .formNodeCountSlider{
                margin-top: -7px;
                padding: 0 10px;
            }
        }
        .IncomeHead{
            text-align: center;
            width: 100%;
            label{
                padding: 10px 0;
            }
            .formNodeCountInput{
                width: 100%;
                border: 1px solid #B4C0D2;
                border-radius: 20px;
                text-align: center;
                height: 42px;
                margin-bottom: -10px;
                margin-top: 10px;
            } 
        }
        .checkBoxLabel{
            padding: 10px 20px 0;
            display: none;
            .checkBoxdiv{
                margin: 0 15px;
            }
        }
    }
}
</style>
