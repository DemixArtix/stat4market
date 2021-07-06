<template lang="pug">
  div(class="header-select d-flex justify-content-center border-r8")
    div(class="header-select__content")
      span(v-if="width > 1200") {{content}}
      span {{accNumber}}
      div(class="header-select__logo" v-html="shopLogo")
</template>

<script>
  export default {
    name: "HeaderSelect",
    props: {
      content: {
        type: String,
        default: ''
      },
      accNumber: {
        type: String,
        default: ''
      },
      shopLogo: {
        type: String,
        default: ''
      },
      width: {
        type: Number,
        default: 0
      }
    }
  }
</script>

<style lang="sass">
  @media screen and (max-width: 576px)
    .header-select
      padding: 8px
</style>