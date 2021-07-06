<template lang="pug">
  div(class="header" ref="header")
    div(class="container-fluid d-flex justify-content-between align-items-center")

      template(v-if="width > 1200")
        HeaderSelect(
          :content="content"
          :accNumber="accNumber"
          :shopLogo="svg.shopLogo"
          :width="width")

        div(class="header-right d-flex")
          HeaderMoney(
            :moneyQuantity="moneyQuantity"
            :countdown="countdown"
            :iconCoin="svg.iconCoin"
            :width="width"
            )
          div(class="header-right__desktop d-flex justify-content-center align-items-center")
            div(class="header-bell d-flex")
              div(class="header-bell__icon rounded-header-icon d-flex justify-content-center align-items-center" v-html="svg.bell")
              div(class="header-bell__counter") {{bellCounter}}
            div(class="header-user d-flex align-items-center")
              div(class="header-user__ava")
                div(class="header-user__icon rounded-header-icon d-flex justify-content-center align-items-center" v-html="svg.user")
              div(class="header-user__name d-flex align-items-center")
                div(class="header-user__text") {{userName}}
                div(class="header-user__arrow" v-html="svg.arrowBlue")

      template(v-if="width < 1200 && width > 768")
        HeaderSelect(
          :content="content"
          :accNumber="accNumber"
          :shopLogo="svg.shopLogo"
          :width="width")
        HeaderMoney(
          :moneyQuantity="moneyQuantity"
          :countdown="countdown"
          :iconCoin="svg.iconCoin"
          :width="width"
        )
        div(class="header-right__desktop d-flex justify-content-center align-items-center")
          div(class="header-bell d-flex")
            div(class="header-bell__icon rounded-header-icon d-flex justify-content-center align-items-center" v-html="svg.bell")
            div(class="header-bell__counter") {{bellCounter}}
          div(class="header-user d-flex align-items-center")
            div(class="header-user__ava")
              div(class="header-user__icon rounded-header-icon d-flex justify-content-center align-items-center" v-html="svg.user")
            div(class="header-user__name d-flex align-items-center")
              div(class="header-user__text") {{userName}}
              div(class="header-user__arrow" v-html="svg.arrowBlue")

      template(v-if="width <= 768")
        div(class="header-icon d-flex align-items-center" v-if="width <= 768")
          div(class="header-icon__logo" v-html="svg.mainLogo")
          div(class="header-icon__text"  v-if="width >= 614") stat<span>4</span>market
        HeaderSelect(
          :content="content"
          :accNumber="accNumber"
          :shopLogo="svg.shopLogo"
          :width="width"
          )
        HeaderMoney(
          :moneyQuantity="moneyQuantity"
          :countdown="countdown"
          :iconCoin="svg.iconCoin"
          :width="width"
        )

        div(
          class="header-right__burger d-flex align-items-center"
          @click="showMobileMenu = !showMobileMenu"
          )
          div(class="header-right__burger_icon" :class="{ 'active': showMobileMenu }")

        transition(name="fade")
          div(class="header-right__tablet d-flex" v-if="showMobileMenu" :style="{'top': headerHeight + 'px'}")
            div(class="header-right__overlay")
            div(class="header-right__menu")
              div(class="header-user menu-item d-flex ")
                div(class="header-user__ava")
                  div(class="header-user__icon d-flex justify-content-center align-items-center" v-html="svg.user")
                div(class="header-user__name d-flex align-items-center")
                  div(class="header-user__text") {{userName}}
              div(class="header-bell menu-item d-flex align-items-center ")
                div(class="header-bell__icon d-flex justify-content-center align-items-center" v-html="svg.bell")
                div(class="header-bell__text") Уведомления
                div(class="header-bell__counter position-relative") {{bellCounter}}




</template>

<script>

  import HeaderSelect from "./HeaderSelect";
  import HeaderMoney from "./HeaderMoney";
  export default {
    name: "Header",
    components: {HeaderSelect, HeaderMoney},
    mounted() {
      this.headerHeight = this.$refs.header.clientHeight;
      console.dir(this.headerHeight);
    },
    data: () =>  ({
      content: 'Ozon',
      accNumber: '(№28451)',
      moneyQuantity: '9932',
      countdown: '345',
      bellCounter: 11,
      userName: 'Александр',
      headerHeight: '',
      showMobileMenu: false,
      svg: {
        mainLogo: '<svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg"><mask id="mask0" mask-type="alpha" maskUnits="userSpaceOnUse" x="0" y="0" width="32" height="32"><circle cx="16" cy="16" r="16" fill="url(#paint0_linear)"/></mask><g mask="url(#mask0)"><circle cx="16" cy="16" r="16" fill="url(#paint1_linear)"/><path d="M21.088 20.44V2.656C21.088 2.384 21.096 2.088 21.112 1.768C21.144 1.448 21.176 1.12 21.208 0.783998L6.52 20.44H21.088ZM34.6841 20.44V21.688C34.6841 21.864 34.6281 22.008 34.5161 22.12C34.4201 22.216 34.2601 22.264 34.0361 22.264H23.104V32.008H21.088V22.264H5.032C4.792 22.264 4.608 22.216 4.48 22.12C4.352 22.008 4.264 21.864 4.216 21.688L4 20.56L21.064 -2H23.104V20.44H34.6841Z" fill="white"></path></g><defs><linearGradient id="paint0_linear" x1="36.8" y1="-9.6" x2="9.2" y2="32" gradientUnits="userSpaceOnUse"><stop stop-color="#FF00AA"/><stop offset="1" stop-color="#8912DE"/></linearGradient><linearGradient id="paint1_linear" x1="36.8" y1="-9.6" x2="9.2" y2="32" gradientUnits="userSpaceOnUse"><stop stop-color="#FF00AA"/><stop offset="1" stop-color="#8912DE"/></linearGradient></defs></svg>',
        arrowBlue: '<svg width="10" height="6" viewBox="0 0 10 6" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M1.35355 0.646447C1.15829 0.451184 0.841709 0.451184 0.646447 0.646447C0.451184 0.841709 0.451184 1.15829 0.646447 1.35355L1.35355 0.646447ZM5 5L4.64645 5.35355L5 5.70711L5.35355 5.35355L5 5ZM9.35355 1.35355C9.54882 1.15829 9.54882 0.841709 9.35355 0.646447C9.15829 0.451184 8.84171 0.451184 8.64645 0.646447L9.35355 1.35355ZM0.646447 1.35355L4.64645 5.35355L5.35355 4.64645L1.35355 0.646447L0.646447 1.35355ZM5.35355 5.35355L9.35355 1.35355L8.64645 0.646447L4.64645 4.64645L5.35355 5.35355Z" fill="#5068A5"/></svg>',
        shopLogo: '<svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><rect width="16" height="16" rx="4" fill="#0069FF"/><g clip-path="url(#clip0)"><path fill-rule="evenodd" clip-rule="evenodd" d="M2.68314 6.00855C2.3684 5.9754 2.05112 6.04054 1.7749 6.19503C1.49869 6.34951 1.2771 6.58576 1.1406 6.87129C1.0041 7.15682 0.95938 7.47762 1.0126 7.78959C1.06581 8.10157 1.21435 8.3894 1.43779 8.61354C1.66123 8.83767 1.9486 8.98709 2.26041 9.04127C2.57222 9.09546 2.89316 9.05173 3.17911 8.91611C3.46506 8.78049 3.70199 8.55964 3.85733 8.2839C4.01267 8.00816 4.07879 7.69108 4.04661 7.37624C4.0112 7.02628 3.85628 6.6992 3.60794 6.45009C3.35959 6.20098 3.033 6.04505 2.68314 6.00855ZM2.6335 8.34268C2.46423 8.36539 2.29209 8.33449 2.14128 8.25431C1.99048 8.17414 1.86859 8.04872 1.79274 7.8957C1.71689 7.74267 1.6909 7.56972 1.71842 7.40116C1.74594 7.2326 1.82559 7.0769 1.94617 6.95594C2.06675 6.83498 2.2222 6.75485 2.39067 6.7268C2.55915 6.69875 2.73218 6.7242 2.88544 6.79957C3.0387 6.87494 3.1645 6.99644 3.24514 7.14699C3.32579 7.29755 3.35723 7.46959 3.33505 7.63893C3.31178 7.81706 3.23043 7.98254 3.10361 8.10976C2.97678 8.23698 2.81155 8.31885 2.6335 8.34268ZM4.86595 6.06916C4.81282 6.06928 4.76039 6.08125 4.71247 6.1042C4.66454 6.12714 4.62234 6.16048 4.58892 6.20178C4.55551 6.24309 4.53172 6.29133 4.51929 6.34299C4.50687 6.39464 4.50611 6.44842 4.51709 6.50041C4.5507 6.66882 4.70801 6.7839 4.87938 6.7839H5.87384L4.32622 8.83196C4.31478 8.84708 4.30777 8.86509 4.30598 8.88397C4.3042 8.90285 4.30771 8.92185 4.31612 8.93885C4.32453 8.95585 4.33751 8.97016 4.3536 8.9802C4.36969 8.99023 4.38826 8.99559 4.40722 8.99566H6.83481C7.00606 8.99566 7.16349 8.88062 7.1971 8.71217C7.20808 8.66019 7.20733 8.60642 7.19491 8.55477C7.1825 8.50312 7.15873 8.45489 7.12533 8.41358C7.09193 8.37227 7.04974 8.33892 7.00183 8.31596C6.95392 8.29301 6.9015 8.28102 6.84838 8.28086H5.6367L7.18313 6.23439C7.19469 6.21912 7.20176 6.20094 7.20356 6.18187C7.20536 6.16281 7.20181 6.14362 7.19331 6.12646C7.18481 6.1093 7.1717 6.09485 7.15545 6.08473C7.13919 6.07461 7.12044 6.06921 7.10129 6.06916H4.86595ZM14.5665 6.0774C14.4861 6.09651 14.4146 6.14248 14.3639 6.2077C14.3132 6.27293 14.2863 6.3535 14.2876 6.4361V7.62612L12.3594 6.09163C12.3442 6.07963 12.326 6.07214 12.3068 6.07002C12.2876 6.0679 12.2682 6.07125 12.2509 6.07967C12.2335 6.08809 12.2189 6.10124 12.2086 6.11761C12.1984 6.13399 12.193 6.15292 12.193 6.17222V8.62935C12.1917 8.71195 12.2187 8.79253 12.2694 8.85776C12.3201 8.92298 12.3915 8.96895 12.4719 8.98805C12.5241 8.99954 12.5782 8.99916 12.6302 8.98694C12.6822 8.97473 12.7308 8.95099 12.7725 8.91748C12.8141 8.88397 12.8477 8.84154 12.8707 8.79333C12.8937 8.74511 12.9057 8.69234 12.9056 8.6389V7.43858L14.8339 8.9731C14.849 8.98509 14.8672 8.99258 14.8864 8.99469C14.9056 8.99681 14.925 8.99347 14.9423 8.98505C14.9597 8.97663 14.9743 8.96349 14.9846 8.94712C14.9948 8.93075 15.0002 8.91183 15.0001 8.89253V6.42644C15.0002 6.37301 14.9883 6.32026 14.9652 6.27206C14.9422 6.22386 14.9086 6.18145 14.867 6.14795C14.8254 6.11445 14.7767 6.09073 14.7247 6.07851C14.6727 6.0663 14.6186 6.06592 14.5665 6.0774ZM9.54575 6.71548C10.3614 6.71548 10.9708 7.1465 10.9708 7.53205C10.9708 7.91759 10.3614 8.34861 9.54575 8.34861C8.73014 8.34861 8.12073 7.91759 8.12073 7.53205C8.12073 7.1465 8.73014 6.71548 9.54575 6.71548ZM9.54575 6.00077C8.36519 6.00077 7.40819 6.68635 7.40819 7.53205C7.40819 8.37774 8.36519 9.06332 9.54575 9.06332C10.7263 9.06332 11.6833 8.37774 11.6833 7.53205C11.6833 6.68635 10.7263 6.00077 9.54575 6.00077Z" fill="white"/></g><defs><clipPath id="clip0"><rect width="14" height="3.06452" fill="white" transform="translate(1 6)"/></clipPath></defs></svg>',
        iconCoin: '<svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M13.6569 2.34313C12.1459 0.832125 10.1369 0 8 0C5.86312 0 3.85406 0.832125 2.34313 2.34313C0.832156 3.85413 0 5.86312 0 8C0 10.1369 0.832156 12.1459 2.34313 13.6569C3.85413 15.1679 5.86312 16 8 16C10.1369 16 12.1459 15.1679 13.6569 13.6569C15.1678 12.1459 16 10.1369 16 8C16 5.86312 15.1678 3.85406 13.6569 2.34313ZM8 15.0625C4.10563 15.0625 0.9375 11.8944 0.9375 8C0.9375 4.10563 4.10563 0.9375 8 0.9375C11.8944 0.9375 15.0625 4.10563 15.0625 8C15.0625 11.8944 11.8944 15.0625 8 15.0625Z" fill="#EA5DBB"/><path d="M8.50226 7.53129H7.49807C6.92598 7.53129 6.46057 7.06589 6.46057 6.49382C6.46057 5.92173 6.92601 5.45632 7.49807 5.45632H9.50641C9.76529 5.45632 9.97516 5.24645 9.97516 4.98757C9.97516 4.7287 9.76529 4.51882 9.50641 4.51882H8.46891V3.48132C8.46891 3.22245 8.25904 3.01257 8.00016 3.01257C7.74129 3.01257 7.53141 3.22245 7.53141 3.48132V4.51882H7.4981C6.40907 4.51882 5.5231 5.40482 5.5231 6.49382C5.5231 7.58282 6.4091 8.46879 7.4981 8.46879H8.50229C9.07435 8.46879 9.53976 8.93423 9.53976 9.50629C9.53976 10.0784 9.07435 10.5438 8.50229 10.5438H6.49395C6.23507 10.5438 6.0252 10.7537 6.0252 11.0125C6.0252 11.2714 6.23507 11.4813 6.49395 11.4813H7.53141V12.5188C7.53141 12.7777 7.74129 12.9876 8.00016 12.9876C8.25904 12.9876 8.46891 12.7777 8.46891 12.5188V11.4813H8.50226C9.59126 11.4813 10.4772 10.5953 10.4772 9.50629C10.4772 8.41729 9.59126 7.53129 8.50226 7.53129Z" fill="#EA5DBB"/></svg>',
        bell: '<svg width="14" height="16" viewBox="0 0 14 16" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M6.83333 1.38667V1.81977L7.26201 1.88155C9.27819 2.17213 10.8333 3.9075 10.8333 6V7.85867C10.8333 9.32464 11.4757 10.7092 12.5953 11.6561C12.7505 11.7897 12.8333 11.9739 12.8333 12.1667C12.8333 12.5339 12.5339 12.8333 12.1667 12.8333H1.16667C0.799475 12.8333 0.5 12.5339 0.5 12.1667C0.5 11.972 0.584316 11.7884 0.732203 11.6613C1.8573 10.7094 2.5 9.32509 2.5 7.85867V6C2.5 3.90744 4.05454 2.17213 6.0713 1.88156L6.5 1.81979V1.38667V0.666667C6.5 0.574468 6.57448 0.5 6.66667 0.5C6.75885 0.5 6.83333 0.574468 6.83333 0.666667V1.38667Z" stroke="#5068A5"/><mask id="path-2-inside-1" fill="white"><path d="M6.66808 16C7.87542 16 8.88542 15.1393 9.11742 14H4.21875C4.45075 15.1393 5.46075 16 6.66808 16Z"/></mask><path d="M6.66808 16C7.87542 16 8.88542 15.1393 9.11742 14H4.21875C4.45075 15.1393 5.46075 16 6.66808 16Z" fill="#5068A5"/><path d="M9.11742 14L30.0218 18.2567L35.2326 -7.33333H9.11742V14ZM4.21875 14V-7.33333H-21.8964L-16.6856 18.2567L4.21875 14ZM6.66808 37.3333C18.2361 37.3333 27.8104 29.1167 30.0218 18.2567L-11.7869 9.74329C-10.0395 1.16192 -2.48527 -5.33333 6.66808 -5.33333V37.3333ZM9.11742 -7.33333H4.21875V35.3333H9.11742V-7.33333ZM-16.6856 18.2567C-14.4742 29.1167 -4.89994 37.3333 6.66808 37.3333V-5.33333C15.8214 -5.33333 23.3757 1.16192 25.1231 9.74329L-16.6856 18.2567Z" fill="#5068A5" mask="url(#path-2-inside-1)"/></svg>',
        user: '<svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M11.9498 9.05034C11.1874 8.28794 10.2799 7.72353 9.28977 7.38187C10.3502 6.65149 11.0469 5.42914 11.0469 4.04701C11.0469 1.81556 9.23148 0.00012207 7.00003 0.00012207C4.76858 0.00012207 2.95314 1.81556 2.95314 4.04701C2.95314 5.42919 3.64983 6.65154 4.71031 7.38187C3.72019 7.72353 2.8127 8.28794 2.05027 9.05034C0.72814 10.3725 0 12.1303 0 14.0001H1.09375C1.09375 10.7435 3.74329 8.09385 7.00003 8.09385C10.2568 8.09385 12.9063 10.7434 12.9063 14.0001H14.0001C14.0001 12.1303 13.2719 10.3724 11.9498 9.05034ZM7.00003 7.00009C5.37167 7.00009 4.04689 5.67534 4.04689 4.04696C4.04689 2.41858 5.37167 1.09382 7.00003 1.09382C8.62838 1.09382 9.95316 2.41858 9.95316 4.04696C9.95316 5.67534 8.62838 7.00009 7.00003 7.00009Z" fill="#5068A5"/></svg>',
      }
    }),
    props: {
      width: {
        type: Number,
        default: 0
      }
    },

  }
</script>

<style lang="sass">
  @import "../assets/styles/colors"

  .fade-enter-active, .fade-leave-active
    transition: opacity .5s
  .fade-enter, .fade-leave-to
    opacity: 0

  .border-r8
    border: 1px solid $mediumBlue
    border-radius: 8px
  .rounded-header-icon
    width: 44px
    height: 44px
    border-radius: 50%
    background-color: $lightBlue


  .header
    padding: 18px 0
    background-color: #fff

    box-shadow: 0px 5px 10px rgba(186, 192, 209, 0.2)
  .header-select
    max-width: 250px
    padding: 12px 16px

  .header-money
    padding: 8px 16px
    margin-right: 40px

  .header-icon
    &__text
      margin-left: 8px
      font-size: 16px
      font-weight: bold
      span
        font-size: inherit
        font-weight: inherit
        color: $pink

  .header-money__button
    padding: 4px 12px
  .header-money__icon,.header-money__quantity
    margin-right: 8px
  .header-money__countdown
    padding-right: 16px
    color: $greyText
  .header-select__content
    margin-left: calc(16px + 6px )
    position: relative
  .header-select__logo
    position: absolute
    right: calc(100% + 6.5px)
    top: 50%
    transform: translateY(-50%)
  .header-bell
    position: relative
    margin-right: 40px
  .header-bell__counter
    position: absolute
    padding: 2px 3px
    background-color: #EA5DBB
    right: 0
    top: 0
    border-radius: 50%
    color: #ffffff
    font-size: 8px
  .header-user__ava
    margin-right: 16px
  .header-user__text
    margin-right: 6px
  .header-right__tablet
    z-index: 9999
    position: absolute
    left: 0
    width: 100%
    height: 100%
  .header-right__overlay
    background-color: black
    opacity: .5
    width: 100%
    height: 100%

  .header-right__menu
    padding: 20px
    background-color: #ffffff
    height: 100%
    width: 300px
    flex-direction: column

    /*& .header-user__icon,.header-bell__icon*/
    /*  background-color: #ffffff*/
  .menu-item
    padding: 15px 0
    border-bottom: 1px solid $lightBlue
    width: 100%
    >div
      &:not(:last-child)
        margin-right: 6px

  .header-right__burger
    width: 24px
    height: 16px
    &_icon
      position: relative
      width: 16px
      height: 2px
      background-color: $blackText
      border-radius: 1px
      transition: .5s
      &:before,&:after
        transition: .5s
        position: absolute
        content: ''
        transform: translateY(-8px)
        height: 2px
        width: 24px
        background-color: $blackText
        border-radius: 1px
      &:after
        transform: translateY(8px)
        width: 20px
      &.active
        background-color: #fff
        width: 0
        border-radius: 0
        &:before
          transform: rotate(45deg)
          top: 50%
        &:after
          width: 24px
          top: 50%
          transform: rotate(-45deg)

  @media screen and (max-width: 1200px)

    .header-select
      max-width: 120px
      padding: 10px 16px
      &__conenet

    .header-money
      padding: 6px 16px
      margin-right: 0
    .header-select,.header-money
      border-radius: 4px

  @media screen and (max-width: 768px)
    .header-money
      margin-right: 0
    .header
      height: 64px
      padding: 12px 0






</style>