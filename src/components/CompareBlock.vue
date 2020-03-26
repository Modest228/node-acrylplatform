<template>
    <section>
        <v-container style="max-width: 1185px;">
            <h2 class="headSection pb-3 secondaryColor" align="left">{{headSection}}</h2>
            <v-data-table
                    :headers="headers"
                    :items="desserts"
                    hide-default-header
                    hide-default-footer
                    class="elevation-1"
            ></v-data-table>
        </v-container>
    </section>
</template>

<script>
    export default {
        data () {
            return {
                headSection: 'Сравнение PoS и PoW',
                headers: [
                    {
                        align: 'start',
                        value: 'name',
                    },
                    { text: 'Acryl', value: 'acryl' },
                    { text: 'Asic', value: 'asic' },
                ],
                desserts: [
                    {
                        name: 'АЛГОРИТМ',
                        acryl: 'POS (ACRYL)',
                        asic: 'POW (ASIC)',
                    },
                    {
                        name: 'Потребление',
                        acryl: '~ 60 Вт',
                        asic: '~ 3000 Вт',
                    },
                    {
                        name: 'Уровень шума',
                        acryl: '~ 0,5 - 1,5 дБА',
                        asic: '~ 80 дБА',
                    },
                    {
                        name: 'Требуется охлаждение',
                        acryl: 'Нет',
                        asic: 'Да',
                    },
                    {
                        name: 'Масса',
                        acryl: '~ 1 кг',
                        asic: '~ 10 кг',
                    },
                    {
                        name: 'Размеры',
                        acryl: '200 x 35 x 200 мм',
                        asic: '298 x 175 x 304 мм',
                    },
                    {
                        name: 'Участие в pool / Пониманимание протоколов',
                        acryl: 'Нет',
                        asic: 'Да',
                    },
                    {
                        name: 'Тонкая настройка',
                        acryl: 'Нет',
                        asic: 'Да',
                    },
                ],
            }
        },
    }
</script>