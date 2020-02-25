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
                            name="name"
                            required></v-text-field>
                        <v-text-field
                            v-model="email"
                            name="email"
                            label="Электронная почта"
                            required></v-text-field>
                        <v-text-field
                            v-model="phone"
                            label="Телефон"
                            name="phone"
                            required></v-text-field>
                        <div class="d-flex align-center ">
                            <v-btn rounded color="primary secondaryColor" @click="formSend()">Заказать</v-btn>
                        </div>
                        <div class="responseError">
                            <p class="errorMessage" v-if='errorMessage'>{{errorMessage}}</p>
                            <p class="response" v-if='response'>{{response}}</p>
                        </div>
                    </div>
                </v-col>
            </v-row>
        </v-container>
    </section>
</template>

<script>
import axios from 'axios'

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
            response: '',
            errorMessage: ''
      }
  },
    methods: {
        formSend: function() {
            if (this.name == '' || this.phone == '' || this.email == '') {
                console.log("Запони все поля")
                this.errorMessage = 'Заполните все поля'
                this.response = ''
            } else {
                let formData = new FormData();
                formData.append('fields[name_1]', this.name)
                formData.append('fields[543953_1][907777]', this.phone)
                formData.append('fields[543955_1][907789]', this.email)
                formData.append('form_id', "585211")
                formData.append('hash', "9b47fca870a99ee10cbd330676441105")

                axios.post('https://forms.amocrm.ru/queue/add', formData, { })
                .then((response) => {
                    console.log("response", response)
                    this.errorMessage = ''
                    this.response = 'Мы с вами свяжемся в ближайшее время'
                    this.name = ''
                    this.phone = ''
                    this.email = ''
                })
                .catch((error) => {
                    console.log(error);
                    this.errorMessage = ''
                    this.response = 'Мы с вами свяжемся в ближайшее время'
                    this.name = ''
                    this.phone = ''
                    this.email = ''
                });
            }
        },
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
    .responseError{
        padding-top: 10px;
        .errorMessage{
            color: red;
        }
        .response{
            color: $secondaryColor;
        }
    }
}

</style>