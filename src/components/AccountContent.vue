<template lang="pug">
  div(class="acc-content")
    div(class="container-fluid")
      div(class=" acc-content-canvas")
        h2(class="acc-title title-h2 mb-4") {{title}}
        div(
          class="horizontal-scroll-wrapper"
          :style="{'width': (width - 150) + 'px'}"
        )
          div(
            class="acc-menu d-flex"
          )
            div(
              class="acc-menu__item"
              v-for="(item, index) of menu"
              :class="[index === 2 ? 'active' : '']"
              :key="index") {{item}}
        div(class="acc-tariffs row")
          div(class="acc-tariffs__item"
            :class="[ index <= 1 ? 'col-xl-4 col-lg-6 col-sm-12' : 'col-xl-4 col-lg-12 col-sm-12' ]"
            v-for="({title: {text, bg}, description, variables}, index) of tariffs" :key="index")
            div(class="acc-tariffs__card")
              div(class="acc-tariffs__title fz18 text-center" :style="bg") {{text}}
              div(class="acc-tariffs__content")
                div(class="acc-tariffs__description" v-html="description")
                table(class="acc-tariffs__variables")
                  tr(class="acc-tariffs__variables_row head")
                    th(class="acc-tariffs__variables_head") Количество товаров
                    th(class="acc-tariffs__variables_head") Месяц
                    th(class="acc-tariffs__variables_head") День
                  tr(class="acc-tariffs__variables_row data"
                    v-for="({quantity, perMonth, perDay}, indexVar) of variables" :key="indexVar")
                    td(class="acc-tariffs__variables_data") {{quantity}}
                    td(class="acc-tariffs__variables_data rubl-font") {{perMonth}}
                      span ₽
                    td(class="acc-tariffs__variables_data rubl-font") {{perDay}}
                      span ₽






</template>

<script>
  export default {
    name: "AccountContent",
    data: () => ({
      title: 'Оплата',
      menu: ['Пополнение баланса', 'Детализация расходов', 'Тарифы, доп. услуги', 'История платежей'],
      tariffs: [
        {
          title: {
            text: 'Wildberries — Аналитика',
            bg: 'background: linear-gradient(88.34deg, #DD50DA 0%, #FF94FD 100%);'
          },
          description: '<p>Анализ заказов, продаж, остатков, товарная аналитика по каждому складу маркетплейса</p>',
          variables: [
            {
              quantity: 'до 50',
              perMonth: '2 370',
              perDay: '79'
            },
            {
              quantity: 'от 51 до 100 ',
              perMonth: '2 970',
              perDay: '99'
            },
            {
              quantity: 'от 101 до 500',
              perMonth: '4 470',
              perDay: '149'
            },
            {
              quantity: 'от 501 до 1000',
              perMonth: '7 470',
              perDay: '249'
            },
            {
              quantity: 'от 1001 до 5000',
              perMonth: '10 470',
              perDay: '349'
            },
            {
              quantity: 'Безлимитный от 5001',
              perMonth: '14 970',
              perDay: '499'
            },

          ]
        },
        {
          title: {
            text: 'Wildberries — Анализ категорий',
            bg: 'background: linear-gradient(88.34deg, #EB5757 0%, #FF8D8D 100%);'
          },
          description: '<p>Анализ любых категорий, страниц брендов, поисковых запросов, акций. Безлимитный доступ к данным по всем товарам со страницы, заказам, остатках на складах, скорости заказов и другим метрикам.</p> <p class="pink">Добавление страницы в отслеживание — 99₽/страница</p> <p>Списывается за уникальную страницу, если вдруг удалили страницу и добавили заново — повторно оплата не снимается</p> <p><strong>Ежедневный мониторинг и обновление страниц:</strong></p>',
          variables: [
            {
              quantity: 'до 3',
              perMonth: '0',
              perDay: '0'
            },
            {
              quantity: 'от 4 до 10 ',
              perMonth: '0',
              perDay: '0'
            },
            {
              quantity: 'от 11 до 20',
              perMonth: '0',
              perDay: '0'
            },
            {
              quantity: 'от 21 до 50',
              perMonth: '0',
              perDay: '0'
            },
            {
              quantity: 'Безлимитный от 51 ',
              perMonth: '0',
              perDay: '0'
            },

          ]
        },
        {
          title: {
            text: 'Wildberries — Позиции товаров',
            bg: 'background: linear-gradient(88.34deg, #6065A7 0%, #8B91DD 100%);'
          },
          description: '<p>Анализ позиций любых товаров на страницах категорий, бренда, поисковых запросов, акций.</p> <p class="pink">Добавление нового товара — 29₽/товар</p> <p>Списывается за уникальный товар, если вдруг удалили товар и добавили заново - повторно оплата не списывается.</p> <strong>Ежедневный мониторинг позиций:</strong>',
          variables: [
            {
              quantity: 'до 20',
              perMonth: '870',
              perDay: '29'
            },
            {
              quantity: 'от 21 до 100 ',
              perMonth: '1 470',
              perDay: '49'
            },
            {
              quantity: 'от 101 до 500',
              perMonth: '2 970',
              perDay: '99'
            },
            {
              quantity: 'от 501 до 1000',
              perMonth: '4 470',
              perDay: '149'
            },
            {
              quantity: 'от 1001 до 5000',
              perMonth: '7 470',
              perDay: '249'
            },
            {
              quantity: 'Безлимитный от 5001',
              perMonth: '8 970',
              perDay: '299'
            },

          ]
        }


      ],
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

  .pink
    color: $pink

  .acc-content-canvas
    background-color: white
    border-radius: 8px
    padding: 30px
  .acc-menu__item
    color: $mainBlue
    &:not(:last-child)
      margin-right: 40px
    &.active
      color: $pink
      border-bottom: 2px solid $pink
  .acc-menu
    border-bottom: 1px solid #EFF1F6
    width: fit-content
    margin-bottom: 32px
  .acc-title

  .acc-tariffs
    &__item

      &.col
        padding: 0
      &:not(:last-child)
        /*margin-right: 32px*/
    &__card
      border-radius: 8px
      background-color: $cardBG
      height: 100%
    &__title
      color: #ffffff
      padding: 16px
      border-radius: 8px 8px 0 0
    &__content
      padding: 24px
    &__description
      p
        margin-bottom: 14px
        &:last-child
          margin-bottom: 16px
    &__variables
      &_row
        border-bottom: 1px solid #ebebeb
      &_head
        padding-top: 14px
        padding-bottom: 14px
        width: 84px
        font-size: 12px
        text-transform: uppercase
        color: $greyText
        &:first-child
          width: 180px
        &:not(:last-child)
          margin-right: 48px

      &_data
        padding-top: 14px
        padding-bottom: 14px
        span
          margin-left: 1px


  .horizontal-scroll-wrapper
    overflow-x: hidden
  .acc-menu
    overflow-x: auto
  @media screen and (max-width: 768px)

    .acc-menu__item
      height: 22px
      width: 150px
      &:not(:last-child)
        margin-right: 16px
    .acc-title.title-h2
      font-size: 18px
      margin-bottom: 26px !important
    .acc-tariffs__variables
      table-layout: fixed
      width: 100%


</style>