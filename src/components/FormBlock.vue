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
                        <v-checkbox v-model="agreeCheck" >
                            <template v-slot:label>
                                <span @click.stop  class="agreeCheckLabel" v-html="agreeCheckLabel"></span>
                            </template>
                        </v-checkbox>
                        <div class="d-flex align-center ">
                            <v-btn rounded color="primary secondaryColor" @click="formSend()">Заказать</v-btn>
                        </div>
                    </div>
                </v-col>
            </v-row>
        </v-container>
        <div class='modalOpen' v-if="modalTrue">
            <div class="modalCards">
                <v-card
                class="modalCard"
                max-width="344"
                max-height="344"
                outlined
                >
                <p class="errorMessage" v-if='errorMessage'>{{errorMessage}}</p>
                <p class="response" v-if='response'>{{response}}</p>    
                <v-btn rounded outlined @click="reversModal()">Закрыть</v-btn>
                </v-card>
            </div>
        </div>
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
            errorMessage: '',
            modalTrue: false,
            agreeCheckLabel: `
                Нажимая кнопку «Отправить», я даю
                согласие на обработку своих
                персональных данных в соответствии с
                <a style="color: #2EA9FB;" href="/#/privacy">Политикой конфиденциальности</a>, а также
                соглашаюсь получать информацию о
                скидках и специальных предложениях на
                указанный e-mail и телефон.`,
            agreeCheck: false,
      }
  },
    methods: {
        formSend: function() {

            if(!this.agreeCheck){
                this.modalTrue = true;
                this.errorMessage = 'Вы не согласились с обработкой персональных данных';
            }else{
                this.Submit_order();
                if (this.name == '' || this.phone == '' || this.email == '') {
                    // console.log("Запони все поля")
                    this.errorMessage = 'Заполните все поля'
                    this.response = ''
                    this.modalTrue = true;
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
                        this.modalTrue = true;
                        this.name = ''
                        this.phone = ''
                        this.email = ''
                    })
                    .catch((error) => {
                        console.log(error);
                        this.errorMessage = ''
                        this.response = 'Мы с вами свяжемся в ближайшее время'
                        this.modalTrue = true;
                        this.name = ''
                        this.phone = ''
                        this.email = ''
                    });
                }
            }
        },
        reversModal: function() {
            this.modalTrue = !this.modalTrue;
            this.errorMessage = '';
            this.response = ''
        },
        Submit_order(){
            console.log("Submit_order")
            window.gaSendButton("Submit_order");
            window.yaSendButton("Submit_order");
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
.agreeCheckLabel{
    font-size: 12px;
    line-height: 16px;
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
.modalOpen{
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.7);
  z-index: 1000;
  .modalCards{
    position: relative;
    width: 100%;
    height: 100vh;
    .modalCard{
        margin: 25% auto;
        display: flex;
        flex-direction: column;
        align-content: center;
        align-items: center;
        justify-content: center;
        padding: 20px;
        p{
            text-align: center;
        }
    }
  }
}
</style>