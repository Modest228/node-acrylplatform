<template>
    <section class="faq-block mxw1200" id="faq">
        <v-container>
            <v-row class="height100">
                <v-col cols="12" sm="12">
                    <h2 class="headSection pb-3 secondaryColor" align="left">{{headSection}}</h2>
                    <v-switch class="mswi" style="margin-left: 84%" v-model="switch2" :label="`${switch2t.toString()}`"></v-switch>
                    <v-expansion-panels accordion value="1" flat class="px-0">
                        <v-expansion-panel v-for="(item, i) in answers" :key="`answer${i}`" active-class="active-primary" >
                            <v-expansion-panel-header class="px-2 elevation-2" >{{item.text}}</v-expansion-panel-header>
                            <v-expansion-panel-content class="px-0">
                                <div  class="contentAnswer">
                                    <v-card  class="mx-auto pa-2">
                                        <span class="phoneAnswer" v-html="item.answer"></span>
                                        <a class="phoneAnswer" v-if="item.phone" :href="`tel:${addressItems.numberLink}`">{{addressItems.number}}</a>
                                    </v-card>
                                </div>
                            </v-expansion-panel-content>
                        </v-expansion-panel>
                    </v-expansion-panels>

                    <div  v-if="switch2 === true">

                    <v-expansion-panels accordion value="1" flat class="px-0">
                        <v-expansion-panel v-for="(item, i) in answersv3" :key="`answer${i}`" active-class="active-primary" >
                            <v-expansion-panel-header class="px-2 elevation-2" >{{item.text}}</v-expansion-panel-header>
                            <v-expansion-panel-content class="px-0">
                                <div class="contentAnswer">
                                    <v-card class="mx-auto pa-2">
                                        <span class="phoneAnswer" v-html="item.answer"></span>
                                        <a class="phoneAnswer" v-if="item.phone" :href="`tel:${addressItems.numberLink}`">{{addressItems.number}}</a>
                                    </v-card>
                                </div>
                            </v-expansion-panel-content>
                        </v-expansion-panel>
                    </v-expansion-panels>
                    </div>
                </v-col>
            </v-row>
        </v-container>
    </section>
</template>
<script>
    export default {
        name: 'FaqBlock',
        props: ['addressItems'],
        data(){
            return {
                    switch1: true,
                    switch2: false,
                    switch1t: `Скрыть`,
                    switch2t: `Показать все вопросы`,
                headSection: `FAQ`,
                answers: [
                    {
                        id: 0,
                        text: `Что такое блокчейн?`,
                        answer: `Выстроенная по определённым правилам непрерывная последовательная цепочка блоков, содержащих информацию. Связь между блоками обеспечивается не только нумерацией, но и тем, что каждый блок содержит свою собственную хеш-сумму и хеш-сумму предыдущего блока.`,
                        phone: false
                    },
                    {
                        id: 1,
                        text: `В чем заключается концепция стейкинга?`,
                        answer: `Это замораживание монет на кошельке пользователя для получения права голоса или подтверждения новых записей внесенных в блокчейн. Стейкинг является основой алгоритма PoS и альтернативным способом майнинга криптовалют. Удерживая монеты пользователи могут получать прибыль, не тратясь на покупку дорогостоящих ASIC-майнеров и оплату электроэнергии.`,
                        phone: false
                    },
                    {
                        id: 2,
                        text: `В чем отличие Proof Of Work от Proof Of Stake алгоритмов?`,
                        answer: `Алгоритм Proof-of-Work (доказательство работой) пришел вместе с Bitcoin и применяется для разгадывания блока (майнинга) с помощью специального оборудования. <br>

                        Суть PoW проста: майнер решает сложную криптографическую задачу при помощи своего оборудования, отправляет результат решения в систему, которая сверяет это решение с проверочным шаблоном. <br>

                        Если решения совпали – за выполненную работу майнер получает вознаграждение, при этом размер вознаграждения фиксированный. <br>

                        В качестве альтернативы PoW в майнинге была создана технология (доказательство ставкой)- Proof-of-Stake. <br>

                        Для майнинга по PoS не нужно специальное оборудование. Вам достаточно иметь кошелек и некоторое количество монеты, которая добывается по данной технологии. <br>

                        Суть PoS в том, что подтверждение транзакции (разгадывание блока) происходит кошельком с данной монетой. То есть для майнинга по PoS необходим лишь кошелек с монетой и включенный компьютер.`,
                        phone: false
                    },
                    {
                        id: 3,
                        text: `Какова доходность и цена устройства Acryl Node?`,
                        answer: `В среднем вознаграждение за размещение устройства составляет $150 ежемесячно. Цена устройства на данный момент $1500. Окупаемость наступает примерно на десятый месяц. Также доходность можно увеличить несколькими способами. Свяжись с нашим представителем для получения более развернутой информации:`,
                        phone: true
                    },
                    {
                        id: 4,
                        text: `За счет чего формируется вознаграждение владельцам ACRYL NODE?`,
                        answer: `Держатели устройств Acryl Node формируют распределенную и устойчивую сеть для записи данных бизнеса, а клиенты B2B, в свою очередь, платят за использование блокчейн Acryl.`,
                        phone: false
                    },
                   ],
                answersv2: [
                    {id: 0, text: `Ещё`,
                        answer: ``,
                        phone: false},
                ],
                answersv3: [
                    {
                        id: 5,
                        text: ` Как заказать Acryl Node? Какой срок и условия доставки?`,
                        answer: `Заказать устройство можно, оставив заявку в форме обратной связи или позвонив по номеру: <a style="color: #3C3C40 !important; text-decoration: none;" href="tel:+78005113715">8 (800) 511-3715</a> или написать на почту <a href="mailto:sales@acrylplatform.com">sales@acrylplatform.com</a>. Наши сотрудники помогут вам с оформлением заказа, а также проконсультруют по любым вопросам.
Доставим ваш заказ БЕСПЛАТНО в течение 10 дней во все города, где осуществляет услуги транспортная компания СDЕК:  <a href="https://www.cdek.ru/">https://www.cdek.ru/</a>.
                               <ul>
                               <li>Доставка по РФ занимает до 5 рабочих дней. </li>
                               <li>Доставка по СНГ занимает до 10 рабочих дней.</li>
                               <li>Доставка в остальные страны, по запросу.</li></ul>`,
                        phone: false
                    },
                    {
                        id: 6,
                        text: `Какая сопутствующая документация предоставляется?`,
                        answer: `<ul>
                               <li>Договор поставки;</li>
                               <li>Лицензионный договор;</li>
                               <li>Спецификации;</li>
                               <li>УПД;</li>
                               <li><a href="https://support.acrylminer.com/l_rus/knowledge_base/item/182297?sid=41814">Сертификат соответствия</a></li>
                               </ul>`,
                        phone: false
                    },
                    {
                        id: 7,
                        text: `У меня уже есть Node, что делать дальше?`,
                        answer: `На коробке из-под устройства есть QR-код, просто наведите на него камеру своего мобильного и для вас откроется подробная инструкция. Если остануться вопросы, напишите в тех.поддержку: <a href="mailto:support@acrylplatform.com">support@acrylplatform.com</a> `,
                        phone: false
                    },
                    {
                        id: 8,
                        text: `Какие возможны способы расчета?`,
                        answer: `Мы принимаем различные способы оплаты, чтобы подобрать удобный для вас, свяжитесь с менеджером по номеру: `,
                        phone: true
                    },
                    {
                        id: 9,
                        text: `Как выводить средства?`,
                        answer: `Мы предлагаем пару ACRYL-BTC, ACRYL-USD`,
                        phone: false
                    },
                    {
                        id: 10,
                        text: `Я хочу стать представителем Acryl в своем городе. Это возможно? Какие условия для дилеров вы предоставляете? `,
                        answer: `Да, конечно. Мы рассматриваем возможность открытия новых дилерских центров в городах и странах , где еще не имеем представительства.
                               Подробную информацию можно получить, позвонив нам по номеру: `,
                        phone: true
                    },
                    {
                        id: 11,
                        text: `Я являюсь представителем бизнеса. Могу ли я совершить запись данных в вашей сети?`,
                        answer: `Да, конечно. Чтобы узнать подробности, необходимо связаться с нашим представителем b2b направления по номеру
                                <a style="color: #3C3C40 !important; text-decoration: none;" href="tel:+79678888555">+7-967-8888-555.</a>
                                Также информацию можно получить на сайте <a href="https://enterprise.acrylplatform.com/"> Acryl Enterprise.</a>`,
                        phone: false
                    }
                ]
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../assets/styles/index.scss";
    .faq-block{
        width: 100%;
        display: flex;
        padding: 20px 10px;
        .mapImage{
            background-image: url(/img/FAQ_Node.png);
            width: 100%;
            min-height: 250px;
            @include respond-to(medium-screens) {
                max-height: 300px;
                min-height: 300px;
            }
            height: 100%;
            background-position: top center;
            background-repeat: no-repeat;
            background-size: contain;
        }
    }
    .contentAnswer{
        margin-left: -24px;
        margin-right: -24px;
        a{
            color: $secondaryColor !important;
            text-decoration: none;
        }
    }
    .active-primary{
        button{
            color: $primaryTextColor;
        }
    }
    .height100{
        height: 100%;
    }

    .fade-enter-active, .fade-leave-active {
        transition: opacity .5s;
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
        opacity: 0;
    }
    .theme--light.v-expansion-panels .v-expansion-panel {
        background-color: #fbfbfb;
    }
    .v-expansion-panel-header {
        padding: 0;
    }
</style>