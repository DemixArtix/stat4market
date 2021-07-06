<template lang="pug">
  div(
    class="header-money d-flex align-items-center border-r8"
    :class="{'border-none': width < 650}"
    )
    div(class="header-money__icon" v-html="iconCoin")
    div(class="header-money__quantity") {{separateThousands}} ₽
    div(class="header-money__countdown fz12" v-if="width > 650") (Хватит ~ {{countdown}} дней)
    div(class="header-money__button button fz13" v-if="width > 650") Пополнить
</template>

<script>
  export default {
    name: "HeaderMoney",
    props: {
      moneyQuantity: {
        type: String,
        default: ''
      },
      countdown: {
        type: String,
        default: ''
      },
      iconCoin: {
        type: String,
        default: ''
      },
      width: {
        type: Number,
        default: 0
      }
    },
    computed: {
      separateThousands() {
        const arr = this.moneyQuantity.split('');
        if(this.moneyQuantity > 3) {
          arr.splice(this.moneyQuantity.length - 3, 0, ' ');
          console.log(arr);
        }
        return arr.join('');
      }
    },
  }
</script>

<style lang="sass">
  .border-none
    border: none !important
</style>