<template>
  <v-app id="inspire">
    <!-- NAVICAGTION DRAWER -->
    <v-navigation-drawer fixed left temporary v-model="drawer" class="hidden-md-and-up" style="z-index: 2147483646;">
      <div class="nav-drawer">
        <div class="topBlock">
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="title">
                <div class="logotype">
                  <router-link to="/"><img class="vert-center widthMobil" src='/img/Acryl-Logo.svg' alt="acryl-logo"/></router-link>
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
                  <v-btn rounded color="primary secondaryColor" small href="#targetOffer">Заказать</v-btn>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </div>
      </div>
    </v-navigation-drawer>


    <app-header :menu-items="menuItems" v-on:changeDrawer="changeDrawerReverse"></app-header>

    <!-- PAGES BLOCKS  -->
    <router-view></router-view>
    
    <footer-block :footer-items="menuItems" :addressItems="addressItems"></footer-block>
  </v-app>
</template>

<script>
import AppHeader from '@/components/AppHeader'
import FooterBlock from '@/components/FooterBlock'

export default {
  name: 'App',

  components: {
    AppHeader,
    FooterBlock
  },

  data() {
    return {
      menuItems: [
        // {id: 1, text: "Магазин", link: "https://shop.acrylminer.com/ru/", target: "_blank"},
        {id: 2, text: "Описание", link: "#targetInfo", target: "_self", click: "Click_more"},
       // {id: 3, text: "Поддержка", link: "https://support.acrylminer.com/l_rus/", target: "_blank", click: "Submit_support"},
        {id: 4, text: "Блог", link: "https://medium.com/acrylplatformru", target: "_blank", click: "Sublit_Blog1"},
       // {id: 5, text: "Контакты", link: "#contacts", target: "_self", click: "Click_contact"}
      ],
      drawer: false,
      addressItems: {
        city: "г.Новосибирск",
        address: "ул. Фабричная 17/4 (12,13 этаж)",
        number: "8 (800) 511-3715",
        numberLink: "88005113715",
        email: "sales@acrylplatform.com",
        support: "Поддержка:",
        emailsupport: "support@acrylplatform.com"
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