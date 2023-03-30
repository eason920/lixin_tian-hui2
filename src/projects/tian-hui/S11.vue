<template>
  <div class="relative">
    <section id="sec11">
      <div
        class="boxp"
        data-aos="fade-up"
        data-aos-duration="1000"
        data-aos-delay="0"
        data-aos-once="false"
      >
        <swiper v-if="hasSwiper" :options="swiperOptions11" ref="swipers11">
          <swiper-slide v-for="(item, i) in swipList" :key="'s11' + i">
            <div class="item">
              <div class="text">{{ item }}</div>
            </div>
          </swiper-slide>
          <template v-slot:button-prev>
            <div class="swiper-button-prev" @click="prevBtns11"></div>
          </template>
          <template v-slot:button-next>
            <div class="swiper-button-next" @click="nextBtns11"></div>
          </template>
          <template v-slot:pagination>
            <div class="swiper-pagination"></div>
          </template>
        </swiper>
        <div v-else class="single"></div>
      </div>
      <div class="boxt">
        <div class="deco">
          <div
            class="title"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            飯店精品 幸福莊園
          </div>
          <div
            class="content"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            把家當作一座時尚飯店來思考<br />
            一樓以橢圓曲線為主軸<br />
            規劃迎賓大廳、交誼廳與物業中心<br />
            頂樓有健身房與空中花園<br />
            享受英式下午茶或烤肉野宴<br />
            不用出門在家就能開始度假
          </div>
          <div class="bird"><bird /></div>
        </div>
        <ul class="dot11"
          v-if="hasSwiper"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <li
            v-for="item in 2"
            :key="'dot11' + item"
            @click="fnDotChange(item)"
          ></li>
          <!-- :class="[{ active: dotNow === item }]" -->
        </ul>
      </div>
      <!-- deco vv -->
    </section>
  </div>
</template>

<script>
import { isMobile, isTablet } from '@/utils'
import $ from 'jquery'
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import 'swiper/css/swiper.css'
import butterfly2 from './butterfly2.vue'
import bird from './bird_red.vue'

export default {
  components: {
    Swiper,
    SwiperSlide,
    butterfly2,
    bird
  },

  computed: {
    // dotNow() {
    //   return 1
    // }
  },

  data() {
    return {
      isMobile,
      isTablet,
      swipList: [
        '2禮賓大廳3D示意圖',
        '1禮賓大廳3D示意圖',
      ],
      swiperOptions11: {
        slidesPerView: 1,
        loop: true, // 是否 slide 後循環
        // initialSlide: 0, // 最初 pic index
        // slidesPerView: 'auto',
        spaceBetween: 0,
        autoplay: {
          delay: 1500,
          disableOnInteraction: false // 換頁後是否停止 autoplay
        },
        speed: 1000,
        grabCursor: true,
        pagination: {
          el: '.swiper-pagination',
          clickable: true,
          type: 'bullets'
        },
        on: {
          slideChangeTransitionEnd: function() {
            // console.log(this.activeIndex) // 切換結束時，告訴我現在是第幾個slide
          },
          slideChangeTransitionStart: function() {
            let eq = this.activeIndex
            // console.log(eq)
            if (eq >= 2) {
              eq = eq - 2
            }
            // console.log(eq) // 切換啟動前，告訴我現在是第幾個slide
            $('.dot11 li')
              .removeClass('active')
              .eq(eq)
              .addClass('active')
          }
        }
      },
      hasSwiper: true
    }
  },
  methods: {
    prevBtns11() {
      this.$refs.swipers11.$swiper.slidePrev()
    },
    nextBtns11() {
      this.$refs.swipers11.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      // console.log(eq)
      if (eq >= 2) {
        eq = eq - 2
      }
      // console.log(eq)
      this.$refs.swipers11.$swiper.slideTo(eq)
    }
  }
}
</script>

<style lang="sass" scoped>
@import "src/assets/style/myvar"

// 上下頁
.swiper-button-prev,
.swiper-button-next
  width: 50px
  height: 80px
  &:after
    color: #fff
    // text-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5), 0px 0px 5px rgba(0, 0, 0, 0.5)

@media screen and (max-width: $bp-mb)
  .swiper-button-prev,
  .swiper-button-next
    width: 30px !important
    top: 50%
    transform: translateY(-20%)
    &:after
      font-size: 32px

// 圖片
.swiper-slide
  background:
    position: center
    size: cover
  &:nth-child(1), &:nth-child(3), &:nth-child(5)
    background-image: url('./S11/1.jpg')

  &:nth-child(2), &:nth-child(4), &:nth-child(6)
    background-image: url('./S11/2.jpg')

// 總高
@media screen and (min-width: $bp-pc)
  .swiper-container, // height 1
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 100%
    // max-height: 70vh
@media screen and (max-width: $bp-mb) and (orientation: portrait)
  .swiper-container,
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 106vw

@media screen and (max-width: $bp-mb) and (orientation: landscape)
  .swiper-container,
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 100vh

// --------------------------------
// -- 我內部介面
// --------------------------------
.item
  position: relative

.text
  font:
    size: 14px
  line-height: 1.7
  position: absolute
  right: .5em
  bottom: .3em
  color: #fff
  text-shadow: 0px 0px 5px rgba(0, 0, 0, 0.5), 0px 0px 5px rgba(0, 0, 0, 0.5)
@media screen and (max-width: $bp-mb)
  .text
    font:
      size: 12px
// --------------------------------
// -- by case customize
// --------------------------------
#sec11
  overflow: hidden

.boxp

.boxt
  display: flex
  flex-direction: column

@media screen and (min-width: $bp-pc)
  #sec11
    overflow: hidden
    padding: 7vw 0
  .boxp
    width: 60vw
    height: 33vw // w * 0.75 // height 2
    float: right
  .boxt
    float: left
    width: 35vw
    padding-left: 10vw
    justify-content: flex-end
    height: 100%
    position: relative
@media screen and (max-width: $bp-mb)
  #sec11
    display: flex
    flex-direction: column
  .boxp
    order: 2

  .boxt
    order: 1

// right msg

.boxt
  position: relative
  z-index: 1
  font:
    size: 22px

$pl: 40px
.deco
  position: relative
  color: #fff
  display: flex
  align-items: flex-start
  flex-direction: column
  text-align: left

.title
  color: $c_pink
  // margin: 20px 0 40px
  font:
    size: 1.59em
    weight: bold

.content
  color: #333
  line-height: 1.5
  text-align: justify

@media screen and (min-width: $bp-pc)
  .boxt
    height: 33vw
    // padding-bottom: 7.5vw
  .deco
    margin-bottom: 1vw
    display: flex
    justify-content: flex-end
    height: 100%
    position: relative
  .title
    position: absolute
    left: 0
    top: 0
    width: 0
  .content
    // font-size: 100vw * 22 / 1920
@media screen and (max-width: 1360px)  
  .boxt
    font:
      size: 14px
@media screen and (max-width: 960px)  
  .boxp
    height: 45vw
  .boxt
    height: 45vw
    padding-left: 6vw

@media screen and (max-width: $bp-mb)
  .boxp
    height: auto
  .boxt
    margin: 10vw 6vw 0
    height: auto
    padding-left: 0

  .deco
    margin-bottom: 10vw

  .title
    margin-bottom: 5vw
    font-size: 23px

  .content
    font-size: 100vw * 13 / 375
// dot
.dot11
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot11
    justify-content: flex-end
    margin-bottom: 1vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot11
    margin-bottom: 12vw

// --------------------------------
// bird
.bird
  position: absolute
  z-index: 3
  transform: scaleX(-1)
  

@media screen and (min-width: $bp-pc)
  .bird
    bottom: 7vw
    left: -3.5vw
    width: 6vw

@media screen and (max-width: 960px)  
  .bird
    bottom: 11vw
@media screen and (max-width: $bp-mb)
  .bird
    transform: scaleX(1)
    width: 33vw
    bottom: -50vw
    right: -14vw

// single pic
.single
  width: 100%
  height: 100%

@media screen and (max-width: $bp-mb)
  .single
    height: 106vw
</style>

<style lang="scss">
// ----------------------------
// -- 不可 sass (?!!!!) 也不可 scoped
// ----------------------------
@import 'src/assets/style/myvar';
// 輪撥點點點的顯示 & 美術
.swiper-container-horizontal
  > .swiper-pagination-bullets
  .swiper-pagination-bullet {
  &.swiper-pagination-bullet-active {
    background: #f2f2f2;
  }
}

.swiper-container-horizontal
  > .swiper-pagination-bullets
  .swiper-pagination-bullet {
  display: none;
}

</style>
