<template>
    <v-app-bar app elevate-on-scroll short class="surface" pa-0>
      <v-container h-100 pa-0 align-center d-flex>
        <div class="display1200 h-100">
          <v-toolbar-title>
            <div class="logotype">
              <a href="#topTarget"><img class="vert-center widthMobil" src='/img/Acryl-Logo.svg' alt="acryl-logo"/></a>
            </div>
          </v-toolbar-title>
          <v-spacer></v-spacer>
          <div class="hidden-sm-and-down h-100">
            <v-toolbar-items>
              <div class="d-flex align-center pr-3">
                <a href="tel:88005113715" class="disPrimary">8 (800) 511-37-15</a>
              </div>
              <div class="d-flex align-center pr-3" v-for="(item, i) in getmenuItems" :key="`menuItem${i}`">
                <a :href="`${item.link}`" class="elHover" :target="`${item.target}`" rel="noreferrer noopener">{{item.text}}</a>
              </div>
              <div class="d-flex align-center pl-3">
                <v-btn rounded color="primary secondaryColor" small href="#targetOffer">Заказать</v-btn>
              </div>
            </v-toolbar-items>
          </div>
          <v-app-bar-nav-icon class="hidden-md-and-up" @click.stop="handleDrawer" name="menuDrawer" aria-label="menuDrawer" ></v-app-bar-nav-icon>
        </div>
      </v-container>
    </v-app-bar>
</template>

<script>
export default {
  name: 'AppHeader',
  props: ['menuItems'],
  computed: {
    getmenuItems(){
      return this.menuItems
    }
  },
  methods: {
    handleDrawer: function(){
      this.$emit('changeDrawer');
    }
  }
}
</script>

<style lang="scss" scope>
@import "../assets/styles/index.scss";
.display1200{
  width: 100%;
  max-width: 1200px;
  display: flex;
  margin: 0 auto;
  align-items: center;
}
.h-100{
  height: 100%;
}
.logotype{
  height: 100%;
  display: flex;
  align-items: center;
  overflow: hidden;
  width: 89px;
  @include respond-to(medium-screens) {width: 220px;}
  .widthMobil{
    height: 18px;
    @include respond-to(medium-screens) {height: 29px;}
  }
}
.disPrimary{
  color: #3C3C40 !important;
  text-decoration: none;
  vertical-align: middle;
  font-weight: 300;
  font-size: 16px;
  line-height: 20px;
  font-style: normal;
}
.elHover{
  color: black !important;
  text-decoration: none;
  vertical-align: middle;
  font-weight: 300;
  font-size: 16px;
  line-height: 20px;
  font-style: normal;
  &:hover{
    text-decoration: underline;
  }
}
</style>