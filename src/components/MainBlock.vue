<template>
    <section id="topTarget" class="imgflow">
            <v-row>
                <v-col cols-sm="8" offset-sm="1" sm="8" cols-md="12" offset-md="4">
                    <div class="btnHeaderBlock">
                        <div class="textHeaderBlock">
                            <h1>Получай от 150$<br />в месяц</h1>
                            <p>Разместив мини дата-центр<br /> у себя в квартире!</p>
                        </div>
                        <v-btn rounded color="primary secondaryColor" href="#targetInfo">Подробнее</v-btn>
                    </div>
                </v-col>
            </v-row>
        <div class="imgHeaderBlock"></div>
    </section>
</template>

<script>
export default {
  name: 'HeaderBlock',
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/index.scss";
.imgflow {
    width: 100%;
    max-width: 1650px;
    height: 100vh;
    min-height: 500px;
    max-height: 500px;
    overflow: hidden;
    position: relative; 
    margin: 0 auto;
    padding: 0;
    display: flex;
    justify-content: center;
    @include respond-to(medium-screens) { 
        background-position: top center; 
        max-height: 660px;
        min-height: 660px;
    }
    .btnHeaderBlock{
        position: absolute;
        width: 100%;
        max-width: 1200px; 
        z-index: 4;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-top: 120px;
        @include respond-to(medium-screens) { 
            justify-content: flex-start;
            align-items: flex-start;
            margin-top: 260px;         
        }
        h1, p{
            text-align: center;
            @include respond-to(medium-screens) { text-align: left; }
        }
        h1{
            font-size: 24px;
            line-height: 29px;
            margin-bottom: 17px; 
        }
        p{
            font-size: 16px;
            line-height: 20px;
        }
    }
    .imgHeaderBlock{
        position: absolute;
        z-index: 3;
        bottom: 0;
        background-image: url(/img/headerImage.png);
        background-position: top right 30%;
        background-size: cover;
        background-repeat: no-repeat;
        width: 100%;
        height: 261px;
        @include respond-to(medium-screens) { background-position: top center; height: 480px; }
        @include respond-to(wide-screens) { border-radius: 240px; }
    }
}
</style>
