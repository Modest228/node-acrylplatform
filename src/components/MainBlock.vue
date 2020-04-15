<template>
    <section id="topTarget" class="imgflow">
        <v-row>
            <v-col cols-sm="8" offset-sm="1" sm="8" cols-md="12" offset-md="4">
                <div class="btnHeaderBlock">
                    <div class="textHeaderBlock">
                        <h1>
                            Получай от 150$
                            <br />в месяц
                        </h1>
                        <p>
                            Успей приобрести персональный мини
                            <br />дата-центр по старому курсу доллара
                            <br />до 30 апреля!
                        </p>
                    </div>
                    <v-btn rounded href="#targetOffer" @click="Click_more()">Узнать подробнее</v-btn>
                </div>
            </v-col>
        </v-row>
        <div class="imgHeaderBlock"></div>
        <div class="calc-block" style="z-index: 2222;">
            <v-card class="calc-card">
                <v-container>
                    <v-row>
                        <v-col>
                            <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
                        </v-col>
                    </v-row>
                    <v-row class="formNodeCount">
                        <v-col cols="12" xs="12" sm="12" md="9" class="maxWidth320 CountNodeHead px-3">
                            <label for="formNodecountNode">{{countNodeHead}}</label>
                            <input
                                    id="formNodecountNode"
                                    class="formNodeCountInput"
                                    name="countNode"
                                    type="text"
                                    :value="`${countNode}`"
                                    disabled
                            />
                            <v-slider
                                    v-model="countNode"
                                    track-color="grey"
                                    always-dirty
                                    min="1"
                                    max="30"
                                    class="formNodeCountSlider"
                            ></v-slider>
                        </v-col>
                    </v-row>
                    <v-row class="formNodeCount">
                        <v-col cols="12" xs="12" sm="12" md="9" class="maxWidth320 CountMonthHead px-3">
                            <label for="formNodecountMonth">{{countMonthHead}}</label>
                            <input
                                    id="formNodecountMonth"
                                    class="formNodeCountInput"
                                    name="countMonth"
                                    type="text"
                                    :value="`${countMonth}`"
                                    disabled
                            />
                            <v-slider
                                    v-model="countMonth"
                                    track-color="grey"
                                    always-dirty
                                    min="1"
                                    max="36"
                                    class="formNodeCountSlider"
                            ></v-slider>
                        </v-col>
                    </v-row>
                    <v-row class="formNodeCount">
                        <v-col cols="12" md="9" class="maxWidth320 IncomeHead px-3">
                            <label for="formNodeincome">{{incomeHead}}</label>
                            <input
                                    id="formNodeincome"
                                    class="formNodeCountInput"
                                    name="income"
                                    type="text"
                                    :value="`$${income}`"
                            />
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col style="font-size: 9px" class="checkBoxInput">
                            <v-checkbox
                                    class="fsize"
                                    v-model="checkBoxInput"
                                    :label="`${checkBoxLabel.toString()}`"
                            ></v-checkbox>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col cols="12" class="formNodeCount" style="font-size: 9px; margin-left: 13%;">
                          <div>*Это гипотетическая модель, а не прогноз производительности. В
                              <br>ней не учитываются сборы или налоги. Фактическая доходность
                              <br>может быть больше или меньше, чем указано выше.</div>
                        </v-col>
                    </v-row>
                </v-container>
            </v-card>
        </div>
    </section>
</template>

<script>
    export default {
        name: "HeaderBlock",
        methods: {
            Click_more() {
                console.log("CLICK_ORDER");
                window.gaSendButton("Click_more");
                window.yaSendButton("Click_more");
            }
        }
    };
</script>
<script>
    export default {
        name: "CalcBlock",
        data() {
            return {
                headSection: `Калькулятор доходности`,
                countNodeHead: `Кол-во ACRYL Node`,
                countNode: 1,
                countMonthHead: `Кол-во месяцев`,
                countMonth: 12,
                incomeHead: `Доход`,
                checkBoxLabel: `Получать повышенный доход, сохраняя заработанные монеты на генерирующем балансе устройстве.`,
                checkBoxInput: false
            };
        },
        computed: {
            income() {
                let countNode = this.countNode; //Кол-во нод
                let countMonth = this.countMonth; //Период в месяцах

                let GENERATOR_BALANCE = 800; //Генерирующий баланс на начало периода
                const COURSE_ACRYL = 13; // Курс акрила к доллору
                let INCOME_MONTH = (180 / 1000) * GENERATOR_BALANCE; //Доходность одной ноды в месяц

                let incomeOnMonth = INCOME_MONTH / COURSE_ACRYL; // Доходность одной ноды в месяц в акрилах

                if (this.checkBoxInput) {
                    //1.2737 * month*month + 138.4448 * month + 15.3828  -  Апроксимация графика доходности без снятия накопленной суммы
                    const res =
                        1.2737 * countMonth * countMonth + 138.4448 * countMonth + 15.3828;
                    return (res * countNode).toFixed(0);
                } else {
                    const res = incomeOnMonth * countMonth * COURSE_ACRYL;
                    return (res * countNode).toFixed(0);
                }
            }
        }
    };
</script>


<style lang="scss" scoped>
    @import "../assets/styles/index.scss";
    .calc-block {
        .calc-card {
            margin: auto -210px;
            border-radius: 5px !important;
            background: #fbfbfb;
            min-width: 468px;
            max-width: 468px;
            max-height: 554px;
            // min-height: 554px;
            .checkBoxInput {
                display: flex;
                justify-content: center;
                padding-bottom: 0px;
            }
        }
        .headSection {
            text-align: center;
            //   width: 300px;
            margin: 0 auto 10px;
        }
        .formNodeCount {
            .maxWidth320 {
                max-width: 320px;
                margin: 0 auto;
            }
            .CountNodeHead {
                text-align: center;
                width: 100%;
                label {
                    padding: 10px 0;
                }
                .formNodeCountInput {
                    width: 100%;
                    border: 1px solid #b4c0d2;
                    border-radius: 20px;
                    text-align: center;
                    height: 42px;
                    margin-bottom: -10px;
                    margin-top: 10px;
                    background-color: #ffffff;
                }
                .formNodeCountSlider {
                    margin-top: -9px;
                    padding: 0 10px;
                }
            }
            .CountMonthHead {
                text-align: center;
                width: 100%;
                label {
                    padding: 10px 0;
                }
                .formNodeCountInput {
                    width: 100%;
                    border: 1px solid #b4c0d2;
                    border-radius: 20px;
                    text-align: center;
                    height: 42px;
                    margin-bottom: -10px;
                    margin-top: 10px;
                    background-color: #ffffff;
                }
                .formNodeCountSlider {
                    margin-top: -7px;
                    padding: 0 10px;
                }
            }
            .IncomeHead {
                text-align: center;
                width: 100%;
                label {
                    padding: 10px 0;
                }
                .formNodeCountInput {
                    width: 100%;
                    border: 1px solid #b4c0d2;
                    border-radius: 20px;
                    text-align: center;
                    height: 42px;
                    margin-bottom: -10px;
                    margin-top: 10px;
                    background-color: #ffffff;
                }
            }
            .checkBoxLabel {
                padding: 10px 20px 0;
                display: none;
                .checkBoxdiv {
                    margin: 0 15px;
                }
            }
        }
    }

    .imgflow {
        width: 100%;
        min-width: 1650px;
        overflow: hidden;
        position: relative;
        margin: 0 auto;
        padding: 0;
        display: flex;
        justify-content: center;
        @include respond-to(medium-screens) {
            background-position: top center;
            max-height: 675px;
            min-height: 675px;
        }
        .btnHeaderBlock {
            position: absolute;
            width: 100%;
            max-width: 1200px;
            z-index: 4;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            margin-top: 120px;
            padding-left: 5%;
            @include respond-to(medium-screens) {
                justify-content: flex-start;
                align-items: flex-start;
                margin-top: 114px;
            }
            h1,
            p {
                text-align: center;
                @include respond-to(medium-screens) {
                    text-align: left;
                }
            }
            h1 {
                font-size: 24px;
                line-height: 29px;
                margin-bottom: 17px;
            }
            p {
                font-size: 16px;
                line-height: 20px;
            }
        }
        .imgHeaderBlock {
            position: absolute;
            z-index: 3;
            bottom: 0;
            background-image: url(/img/main_photo.jpg);
            background-position: top right 30%;
            background-size: cover;
            background-repeat: no-repeat;
            width: 100%;
            @include respond-to(medium-screens) {
                background-position: top center;
                height: 675px;
            }
            @include respond-to(wide-screens) {
            }
        }
    }

    .theme--light.v-btn:not(.v-btn--flat):not(.v-btn--text):not(.v-btn--outlined) {
        background-color: #202020;
        border-radius: 5px;
    }
    .theme--light.v-btn:not(.v-btn--flat):not(.v-btn--text):not(.v-btn--outlined):hover {
        background-color: #3c3c40;
    }
    @media (min-width: 601px) {
        .calc-block {
            padding: 100px 27.5%;
        }
        .imgflow {
            height: 100vh;
            min-height: 675px;
            max-height: 675px;
        }
    }
    @media (max-width: 600px) {
        .project-info-block {
            .mapImage {
                visibility: hidden;
            }
        }
        .calc-block {
            padding: 100px 12.5%;
            .calc-card {
                margin: auto -248px;
            }
        }
        .imgflow {
            flex-direction: column;
            .btnHeaderBlock {
                width: 19%;
                margin-top: 65px;
            }
            .imgHeaderBlock {
                height: 100vh;
                background-position: top right 42%;
                position: inherit;
            }
        }
    }
    @media (max-height: 670px) {
.imgflow{
    .imgHeaderBlock {
        background-position: top right 33%;
    }
}
    }
</style>
