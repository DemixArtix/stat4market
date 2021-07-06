<template lang="pug">
  div(class="ad-services")
    div(class="container-fluid")
      h2(class="ad-services__title title-h2") {{title}}:
      div(class="ad-services__subtitle") {{subtitle}}
      div(class="ad-services__list row")
        div(class="ad-services__item"
          v-for="({name, text, benefit, oldPrice, time, currentPrice, img: {big, medium, small}}, index) of services"
          :key="index")
          div(class="ad-services__card d-flex justify-content-between")
            div(class="ad-services__image")
              img(v-if="width > 1200" :src='require(`@/assets/img/${big}`)')
              img(v-if="width <= 1200 && width > 600" :src='require(`@/assets/img/${medium}`)')
              img(v-if="width <= 600" :src='require(`@/assets/img/${small}`)')
            div(class="ad-services__description flex-grow-1 d-flex flex-column")
              h3(class="ad-services__description_title title-h3") {{name}}
              div(class="ad-services__description_text" v-html="text")
              div(class="ad-services__description_benefit mt-auto d-flex align-items-center")
                div
                  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M0 12C0 5.37258 5.37258 0 12 0C18.6274 0 24 5.37258 24 12C24 18.6274 18.6274 24 12 24C5.37258 24 0 18.6274 0 12Z" fill="#A5D274"/>
                  <path d="M7 11.1739L10.913 15.087L17 9" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                span {{benefit}}
            div(class="ad-services__price d-flex align-items-center")
              div(class="ad-services__price_numbers d-flex")
                div(class="ad-services__price_old") {{oldPrice}}
                  span ₽
                div(class="ad-services__price_current") {{currentPrice}}
                  span ₽
                div(class="ad-services__price_time") {{time}}
              div(class="ad-services__price_buttons d-flex")
                div(class="ad-services__price_order button") Заказать
                div(class="ad-services__price_details button-transparent") Подробее об услуге




</template>

<script>
  export default {
    name: "AdditionalServices",
    data: () => ({
      title: 'Дополнительные услуги',
      subtitle: 'Помощь от команды Stat4market, основателя сервиса и партнеров, для увеличения продаж и помощи по работе с маркетплейсом.',
      services: [
        {
          name: 'Оптимизация продаж на маркетплейсе',
          text: '<p>Наш основной продукт для тех, кто уже продаёт на Wildberries, направленный напрямую на увеличение вашей прибыли от работы с маркетплейсом. В нашем сервисе уже несколько сотен поставщиков и мы понимаем основные ошибки поставщиков, которые тормозят их рост и рычаги увеличения ваших продаж на маркетплейсах. Наша команда и основатель сервиса Дмитрий Бакланов проанализирует ваш бренд, найдут точки роста, оптимизации товаров.</p><p>Для начала работы необходимо заполнить заявку по ссылке «Заказать».</p>  ',
          benefit: 'Вы получите полное понимание своих дальнейших действий для развития бренда, также чек-лист из более 30 пунктов по улучшениям или проблемам именно вашего бренда для оптимизации, увеличения выручки и прибыли.',
          oldPrice: '29 900',
          currentPrice: '24 900',
          time: '2 часа',
          img: {
            big: 'img.png',
            medium : 'img3.png',
            small: 'img5.png'
          }
        },
        {
          name: 'Помощь в выходе на маркетплейс',
          text: '<p>Продукт для тех кто только собирается выйти на Wildberries. Состоит из пошагового плана со всеми этапами выхода на маркетплейс до первой поставки а также 2-х часовая консультация с экспертом, ответы на все вопросы. Необходимо предварительно заполнить заявку по ссылке «Заказать».</p>  ',
          benefit: 'Вы получите ответы на все вопросы, которые мешают выйти и поставить ваши товары на Wildberries.',
          oldPrice: '9 900',
          currentPrice: '4 900',
          time: '2 часа',
          img: {
            big: 'img-2.png',
            medium : 'img4.png',
            small: 'img6.png'
          }
        },
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

  .ad-services__title
    margin-top: 48px
    margin-bottom: 16px
  .ad-services__subtitle
    margin-bottom: 24px
  .ad-services__list.row
    --bs-gutter-y: 24px !important
  .ad-services__card
    background-color: #ffffff
    box-shadow: 0 10px 50px rgba(24, 34, 70, 0.1)
    border-radius: 8px
  .ad-services__description
    display: inline-block
    padding: 30px 0 30px 30px
    max-width: 1238px
    &_title
    &_text
      color: $greyText
      p
        color: inherit
    &_benefit
      padding: 16px 20px
      background-color: $cardBG
      border-radius: 4px
      span
        margin-left: 12px

  .ad-services__price
    margin: 30px
    flex-direction: column
    justify-content: center
    &_numbers
      align-items: center
      flex-direction: column
    &_order

      background-color: $mainBlue

    &_details
      border-color: $mediumBlue !important
  .ad-services__price_order,.ad-services__price_details
    padding: 10px
    text-align: center

  .ad-services__price_buttons.row
    --bs-gutter-y: 16px !important
    --bs-gutter-x: 40px !important
  .ad-services__price_numbers.row
    --bs-gutter-y: 8px !important
  .ad-services__price_old,.ad-services__price_current
    font-size: 24px
    font-weight: 600
    span
      font-size: inherit
      font-weight: 400
      color: inherit
  .ad-services__price_old
    color: $mainBlue
    text-decoration: line-through
  .ad-services__price_numbers
    margin-bottom: 24px
    div
      text-align: center
  .ad-services__image
    width: 305px
    display: flex
    align-items: center
    justify-content: center


    img
      border-radius: 8px 0 0 8px
      overflow: hidden
      height: 100%
      object-fit: cover

  .ad-services__price_buttons
    flex-direction: column

    &>div
      width: 210px
    &>div:first-child
      margin-bottom: 16px

  @media screen and (max-width: 1200px)
    .ad-services__card
      flex-direction: column

    .ad-services__image
      width: 100%
      height: 320px
      overflow: hidden
      border-radius: 8px 8px 0 0
      img
        border-radius: 0
        width: 100%
        height: 100%
    .ad-services__price
      flex-direction: row
      justify-content: space-between
      min-width: fit-content
      &_old,&_current
        margin-right: 24px

    .ad-services__price_numbers
      align-items: center
      flex-direction: row
      margin-bottom: 0


    .ad-services__price_numbers>div
      text-align: left


    .ad-services__price_buttons
      flex-direction: row
      width: auto
      &>div
        width: 160px
        padding-left: 0
        padding-right: 0
        &:first-child
          margin-right: 16px
          margin-bottom: 0
    .ad-services__description
      padding: 16px

  @media screen and (max-width: 650px)
    .ad-services__card


    .ad-services__image

    .ad-services__price
      flex-direction: column
      justify-content: space-between
      min-width: fit-content
      margin-bottom: 8px
      margin-top: 0
      &_old,&_current
        margin-right: 0px

    .ad-services__price_numbers
      align-items: center
      flex-direction: column
      margin-bottom: 0


    .ad-services__price_numbers>div
      text-align: center


    .ad-services__price_buttons
      flex-direction: column
      width: 100%
      margin-bottom: 16px
      &>div
        width: 100%
        padding-left: 0
        padding-right: 0
        &:first-child
          margin-right: 0
          margin-bottom: 8px
    .ad-services__description
      padding: 16px


</style>