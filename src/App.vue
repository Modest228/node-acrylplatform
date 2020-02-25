<template>
  <v-app id="inspire">
    <!-- NAVICAGTION DRAWER -->
    <v-navigation-drawer fixed left temporary v-model="drawer" class="hidden-md-and-up">
      <div class="nav-drawer">
        <div class="topBlock">
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="title">
                <div class="logotype">
                  <a href="#topTarget"><img class="vert-center widthMobil" src='/img/Acryl-Logo.svg' alt="acryl-logo"/></a>
                </div>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-divider></v-divider>

          <div v-for="(item, i) in getmenuItems" :key="`drawerMenu${i}`">
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title class="title">
                      <a :href="`${item.link}`" class="elHover" :target="`${item.target}`" rel="noreferrer noopener">{{item.text}}</a>
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
              <v-divider></v-divider>
          </div>
        </div>

        <div class="bottomBlock">
          <v-divider></v-divider>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="title">
                  <a :href="`tel:${addressItems.numberLink}`" class="noDecoration secondaryColor" >{{addressItems.number}}</a>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-divider></v-divider>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="title">
                  <v-btn rounded color="primary secondaryColor" small href="#targetConteiner">Заказать</v-btn>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </div>
      </div>
    </v-navigation-drawer>


    <app-header :menu-items="menuItems" v-on:changeDrawer="changeDrawerReverse"></app-header>
    <main-block></main-block>
    <project-info-block></project-info-block>
    <device-info-block></device-info-block>
    <calc-block></calc-block>
    <how-it-work-block></how-it-work-block>
    <faq-block :addressItems="addressItems"></faq-block>
    <form-block></form-block>
    <map-block :addressItems="addressItems"></map-block>
    <footer-block :footer-items="menuItems" :addressItems="addressItems"></footer-block>
  </v-app>
</template>

<script>
import AppHeader from '@/components/AppHeader'
import MainBlock from '@/components/MainBlock'
import ProjectInfoBlock from '@/components/ProjectInfoBlock'
import DeviceInfoBlock from '@/components/DeviceInfoBlock'
import CalcBlock from '@/components/CalcBlock'
import HowItWorkBlock from '@/components/HowItWorkBlock'
import FaqBlock from '@/components/FaqBlock'
import FormBlock from '@/components/FormBlock'
import MapBlock from '@/components/MapBlock'
import FooterBlock from '@/components/FooterBlock'

export default {
  name: 'App',

  components: {
    AppHeader,
    MainBlock,
    ProjectInfoBlock,
    DeviceInfoBlock,
    CalcBlock,
    HowItWorkBlock,
    FaqBlock,
    FormBlock,
    MapBlock,
    FooterBlock
  },

  data() {
    return {
      menuItems: [
        {id: 1, text: "Магазин", link: "https://shop.acrylminer.com/ru/", target: "_blank"},
        {id: 2, text: "Описание", link: "#targetInfo", target: "_self"},
        {id: 3, text: "Поддержка", link: "https://support.acrylminer.com/l_rus/", target: "_blank"},
        {id: 4, text: "Блог", link: "https://medium.com/acrylplatformru", target: "_blank"},
        {id: 5, text: "Контакты", link: "#contacts", target: "_self"} 
      ],
      // footerItems: [
      //   {id: 1, text: "Магазин", link: "https://shop.acrylminer.com/ru/", target: "_blank"},
      //   {id: 2, text: "Описание", link: "#targetInfo", target: "_self"},
      //   {id: 3, text: "Поддержка", link: "https://support.acrylminer.com/l_rus/", target: "_blank"},
      //   {id: 4, text: "Блог", link: "https://medium.com/acrylplatformru", target: "_blank"},
      //   {id: 5, text: "Контакты", link: "#contacts", target: "_self"},
      // ],
      drawer: false,
      addressItems: {
        city: "г.Новосибирск",
        address: "ул. Фабричная 17/4 (12,13 этаж)",
        number: "8 (800) 511-3715",
        numberLink: "88005113715",
        email: "sales@acrylplatform.com"
      }
    }
  },
  computed: {
    getmenuItems(){
      return this.menuItems
    }
  },
  methods: {
    changeDrawerReverse() {
      this.drawer = !this.drawer;
    }
  }
};
</script>

<style lang="scss" scoped>
@import "./assets/styles/index.scss";
#inspire{
  font-family: $body-font-family !important;
  .nav-drawer{
    position: fixed;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-content: space-between;
    .topBlock{

    }
    .bottomBlock{
      .noDecoration{
        text-decoration: none;
      }
    }
  }
}
.logotype{
  width: 120px;
  margin: 0;
  padding: 0;
  img{
    width: 200px;
    height: auto;
  }
}
.v-btn__content{
    color: $secondaryColor !important;
}
</style>