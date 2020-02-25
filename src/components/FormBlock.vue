<template>
    <section class="form-block mxw1200">
        <div id="targetOffer"></div>
        <v-container>
            <v-row class="height100">
                <v-col cols="12" offset-sm="5" md="7" >
                    <h2 class="headSection pb-3 secondaryColor">{{headSection}}</h2>
                    <div class="maxWidth">
                        <v-text-field
                            v-model="name"
                            label="Имя"
                            required></v-text-field>
                        <v-text-field
                            v-model="email"
                            :rules="emailRules"
                            label="Электронная почта"
                            required></v-text-field>
                        <v-text-field
                            v-model="phone"
                            label="Телефон"
                            required></v-text-field>
                        <div class="d-flex align-center ">
                            <v-btn rounded color="primary secondaryColor">Заказать</v-btn>
                        </div>
                    </div>
                </v-col>
            </v-row>
        </v-container>
    </section>
</template>

<script>
export default {
  name: 'FormBlock',
  data(){
      return {
            headSection: `Заказать`,
            valid: false,
            name: '',
            phone: '',
            email: '',
            emailRules: [
                v => !!v || 'E-mail is required',
                v => /.+@.+/.test(v) || 'E-mail must be valid',
            ],
      }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/styles/index.scss";
#targetOffer{
    position: absolute;
    left: 0;
    right: 0;
    top:-100px;
}
.form-block{
    width: 100%;
    display: flex;
    padding: 20px 10px;
    position: relative;
    .mapImage{
        background-image: url(/img/FAQ_Node.png);
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
    .height100{
        height: 100%;
    }
    .maxWidth{
        max-width: 320px;
    }
}

</style>