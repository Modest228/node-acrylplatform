<template>
    <section>
        <v-container style="max-width: 1185px;">
            <h2 class="headSection pb-3 secondaryColor" align="left">Сравнение PoS и PoW</h2>
            <table class="elevation-1" style="width:100%; background: #fbfbfb; border-radius: 5px;">

            <tr>
                <th style="font-weight: 500" align="left">АЛГОРИТМ</th>
                <th style="font-weight: 500" align="left">POS (ACRYL)</th>
                <th style="font-weight: 500" align="left">POW (ASIC)</th>
            </tr>
            <tr class="feditmob">
                <td>Потребление</td>
                <td class="tdb">~ 60 Вт</td>
                <td>~ 3000 Вт</td>
            </tr>
            <tr class="feditmob">
                <td>Уровень шума</td>
                <td class="tdb">~ 0,5 - 1,5 дБА</td>
                <td>~ 80 дБА</td>
            </tr>
                <tr class="feditmob">
                    <td>Требуется охлаждение</td>
                    <td class="tdb">Нет</td>
                    <td>Да</td>
                </tr>
                <tr class="feditmob">
                    <td>Масса</td>
                    <td class="tdb">~ 1 кг</td>
                    <td>~ 10 кг</td>
                </tr>
                <tr class="feditmob">
                    <td>Размеры</td>
                    <td class="tdb">200 x 35 x 200 мм</td>
                    <td>298 x 175 x 304 мм</td>
                </tr>
                <tr class="feditmob">
                    <td>Участие в pool / Понимание протоколов</td>
                    <td class="tdb">Нет</td>
                    <td>Да</td>
                </tr>
                <tr class="feditmob">
                    <td>Тонкая настройка</td>
                    <td class="tdb">Нет</td>
                    <td>Да</td>
                </tr>
            </table>
        </v-container>
    </section>
</template>

<script>

</script>

<style>
    th, td {
        padding: 15px;
    }
    .tdb {
        font-weight: bold;
    }
    @media (max-width: 600px) {
       .feditmob {
           font-size: 14px;
       }
    }
</style>