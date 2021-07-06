<template lang="pug">
  div(class="nav")
    div(class="container-fluid")

      h1(class="nav-title mb-3" :class="[ width > 768 ? 'fz30' : 'fz20']") {{title}}
      template(v-if="width > 700")
        div(class="nav-menu d-flex ")
          div(class="nav-item" :class="[ index === 1 ? 'button' : 'button-transparent' ]" v-for="(item, index) of menu" :key="index") {{item}}
      template(v-else)
        div(class="nav-menu__mobile")
          div(class="nav-menu__mobile_current d-flex justify-content-between align-items-center" @click="showNav = !showNav")
            span {{currentMobileItem}}
            div(:class="[ showNav ? 'active' : '' ]" v-html="arrow")

          div(class="nav-menu__mobile_list" v-if="showNav")
            div(
              class="nav-menu__mobile_item"
              v-for="(item, index) of menu"
              :key="index"
              v-if="item !== currentMobileItem"
              @click="selectNavItem(item)"
              ) {{item}}


</template>

<script>
  export default {
    name: "Navigation",
    data: () => ({
      title: 'Личный кабинет',
      menu: ['Настройки', 'Оплата', 'Уведомления', 'Партнёрская программа', 'Обучение'],
      currentMobileItem: 'Оплата',
      showNav: false,
      arrow: '<svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M1.35355 0.646447C1.15829 0.451184 0.841709 0.451184 0.646447 0.646447C0.451184 0.841709 0.451184 1.15829 0.646447 1.35355L1.35355 0.646447ZM5 5L4.64645 5.35355L5 5.70711L5.35355 5.35355L5 5ZM9.35355 1.35355C9.54882 1.15829 9.54882 0.841709 9.35355 0.646447C9.15829 0.451184 8.84171 0.451184 8.64645 0.646447L9.35355 1.35355ZM0.646447 1.35355L4.64645 5.35355L5.35355 4.64645L1.35355 0.646447L0.646447 1.35355ZM5.35355 5.35355L9.35355 1.35355L8.64645 0.646447L4.64645 4.64645L5.35355 5.35355Z" fill="#666666"/></svg>'
    }),
    props: {
      width: {
        type: Number,
        default: 0,
      }
    },
    methods: {
      selectNavItem(item) {
        this.currentMobileItem = item;
        this.showNav = false
      }
    }

  }
</script>

<style lang="sass">
  @import "../assets/styles/colors"

  .nav
    margin-top: 27px
    padding-bottom: 24px
  .nav-item
    padding: 10px 16px
    &:not(:last-child)
      margin-right: 16px
  .nav-title
    color: $blackText
    font-weight: 600
    /*margin-bottom: 24px*/
  .nav-menu__mobile_current
    padding: 12px 16px
    background-color: #ffffff
    border: 1px solid $mediumBlue
    border-radius: 4px
    font-size: 12px
    span
      font-size: inherit

  .nav-menu__mobile
    position: relative
  .nav-menu__mobile_current>div
    transition: .5s
  .nav-menu__mobile_current>.active
    transform: rotate(180deg)
  .nav-menu__mobile_list
    position: absolute
    top: calc(100% + 10px)
    left: 0
    width: 100%
    background-color: #ffffff
    border: 1px solid $mediumBlue
    border-radius: 4px
    font-size: 12px
    padding: 2px 16px
  .nav-menu__mobile_item
    padding: 10px 0
    &:not(:last-child)
      border-bottom: 1px solid $lightBlue

  @media screen and (max-width: 768px)
    .nav-title



</style>