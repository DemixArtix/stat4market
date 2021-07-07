<template lang="pug">
  div(id="app" class="content-bg")
    Header(:width="width")
    Navigation(:width="width")
    AccountContent(:width="width")
    AdditionalServices(:width="width")



</template>

<script>

import Header from "./components/Header";
import Navigation from "./components/Navigation";
import AccountContent from "./components/AccountContent";
import AdditionalServices from "./components/AdditionalServices";
export default {
  name: 'App',
  components: {
    AdditionalServices,
    AccountContent,
    Navigation,
    Header
  },
  created() {
    window.addEventListener('resize', this.updateWidth);
    this.width = window.innerWidth;
  },
  data: () => ({
    width: 0
  }),
  methods: {
    updateWidth() {
      console.log(window.innerWidth);
      this.width = window.innerWidth;
    },
  }
}
</script>

<style lang="scss">

  @import "./assets/styles/normalize.css";
  @import "./assets/styles/colors";

@font-face {
  font-family: 'Lato';
  src: url('./assets/fonts/Lato/subset-Lato-Light.eot');
  src: url('./assets/fonts/Lato/subset-Lato-Light.eot?#iefix') format('embedded-opentype'),
  url('./assets/fonts/Lato/subset-Lato-Light.woff2') format('woff2');
  font-weight: 300;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Lato';
  src: url('./assets/fonts/Lato/Lato-Regular.eot');
  src: url('./assets/fonts/Lato/Lato-Regular.eot?#iefix') format('embedded-opentype'),
  url('./assets/fonts/Lato/Lato-Regular.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Lato';
  src: url('./assets/fonts/Lato/Lato-Semibold.eot');
  src: url('./assets/fonts/Lato/Lato-Semibold.eot?#iefix') format('embedded-opentype'),
  url('./assets/fonts/Lato/Lato-Semibold.woff2') format('woff2');
  font-weight: 600;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'Lato';
  src: url('./assets/fonts/Lato/Lato-Heavy.eot');
  src: url('./assets/fonts/Lato/Lato-Heavy.eot?#iefix') format('embedded-opentype'),
  url('./assets/fonts/Lato/Lato-Heavy.woff2') format('woff2');
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'ALS Rubl';
  src: url('./assets/fonts/rouble/rouble.eot');
  src: url('./assets/fonts/rouble/rouble.eot?#iefix') format('embedded-opentype'),
  url('./assets/fonts/rouble/rouble.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}

  .row {
    --bs-gutter-x: 32px !important;
    --bs-gutter-y: 30px !important;
  }


  * {
    margin: 0;
    box-sizing: border-box;
    font-family: 'Lato', sans-serif;
    font-weight: normal;
    font-size: 14px;
    color: $darkText;
  }

  body {

  }

  #app {
    padding-bottom: 86px;
    position: relative;
  }

  .container-fluid {
    max-width: 1900px;
    padding-left: 38px !important;
    padding-right: 38px !important;
  }

  /*.rubl-font {*/
  /*  font-family: 'ALS Rubl', sans-serif;*/
  /*}*/


  .title-h2 {
    font-size: 24px;
    font-weight: 600;
    color: $blackText;
    margin-bottom: 26px;
  }

  .title-h3 {
    font-size: 20px;
    font-weight: 600;
    color: $blackText;
    margin-bottom: 16px;
  }

  .container {
    padding-left: 38px;
    padding-right: 38px;
    width: 1900px;
  }
  .content-bg {
    background-color: $contentBG;
  }

  .button {
    border-radius: 4px;
    background-color: $mainBlue;
    color: #fff;
  }

  .button-transparent {
    border: 1px solid $mainBlue;
    color: $mainBlue;
    border-radius: 4px;
  }

  .fz12 {
    font-size: 12px;
  }
  .fz13 {
    font-size: 13px;
  }

  .fz18 {
    font-size: 18px;
  }
  .fz20 {
    font-size: 20px;
  }

  .fz30 {
    font-size: 30px;
    font-weight: 600;
  }

  @media screen and (max-width: 768px) {
    .container-fluid {
      padding-left: 16px !important;
      padding-right: 16px !important;
    }

  }


</style>
