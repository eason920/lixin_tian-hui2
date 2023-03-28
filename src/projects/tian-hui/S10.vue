<template>
  <div class="relative">
    <section id="sec10">
      <div
        class="boxp"
        data-aos="fade-up"
        data-aos-duration="1000"
        data-aos-delay="0"
        data-aos-once="false"
      >
        <swiper v-if="hasSwiper" :options="swiperOptions10" ref="swipers10">
          <swiper-slide v-for="(item, i) in swipList" :key="'s10' + i">
            <div class="item">
              <div class="text">{{ item }}</div>
            </div>
          </swiper-slide>
          <template v-slot:button-prev>
            <div class="swiper-button-prev" @click="prevBtns10"></div>
          </template>
          <template v-slot:button-next>
            <div class="swiper-button-next" @click="nextBtns10"></div>
          </template>
          <template v-slot:pagination>
            <div class="swiper-pagination"></div>
          </template>
        </swiper>
        <div v-else class="single">
          <div class="text">外觀3D透視圖</div>
          <div class="text_en">
            <img v-if="isMobile" src="./S10/txt_mb.png" />
            <img v-else src="./S10/txt_pc.png" />
          </div>
        </div>
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
            幾何線條 時尚經典
          </div>
          <div
            class="content"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            匯集幾何線條的俐落品味與新時尚美學<br/>
            外觀隨著光線變化表情<br/>
            雕琢出層次感與藝術性<br/>
            石材、玻璃、金屬板之間的完美搭配<br/>
            虛實相間剛柔並蓄<br/>
            提供新世代家庭美好且驕傲的地標居所
          </div>
          <tree2 class="tree t2" />
          <tree3 v-if="!isMobile" class="tree t3" />
          <butterfly1 class="butt"/>
        </div>
        <ul class="dot10"
          v-if="hasSwiper"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <li
            v-for="item in 2"
            :key="'dot10' + item"
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
import butterfly1 from './butterfly1.vue'
import tree2 from './tree2.vue'
import tree3 from './tree3.vue'

export default {
  components: {
    Swiper,
    SwiperSlide,
    butterfly1,
    tree2,
    tree3
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
        '2天母商圈',
        '1天母星巴克',
      ],
      swiperOptions10: {
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
            $('.dot10 li')
              .removeClass('active')
              .eq(eq)
              .addClass('active')
          }
        }
      },
      hasSwiper: false
    }
  },
  methods: {
    prevBtns10() {
      this.$refs.swipers10.$swiper.slidePrev()
    },
    nextBtns10() {
      this.$refs.swipers10.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      // console.log(eq)
      if (eq >= 2) {
        eq = eq - 2
      }
      // console.log(eq)
      this.$refs.swipers10.$swiper.slideTo(eq)
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
    background-image: url('./S4/1.jpg')

  &:nth-child(2), &:nth-child(4), &:nth-child(6)
    background-image: url('./S4/2.jpg')

// 總高
@media screen and (min-width: $bp-pc)
  .swiper-container, // height 1
  .swiper-wrapper,
  .swiper-slide,
  .item
    height: 33vw
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
#sec10

.boxp

.boxt
  display: flex
  flex-direction: column

@media screen and (min-width: $bp-pc)
  #sec10
    overflow: hidden
    padding: 7vw 0
  .boxp // 47 + 8 = 55
    width: 47vw
    height: 51vw
    margin-left: 8vw
    float: left
  .boxt // 100 - 55 = 45
    float: right
    width: 35vw
    padding
      right: 8vw
    justify-content: flex-end
    height: 100%
    position: relative
@media screen and (max-width: $bp-mb)
  #sec10
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

$pl: 40px
.deco
  // padding-left: $pl
  margin-bottom: 5vw
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
    size: 28px
    weight: bold

.content
  color: #333
  font:
    size: 100vw * 18 / 1920
    weibht: bold
  line-height: 1.5
  text-align: justify

.bird
  position: absolute
  img
    width: 100%

@media screen and (min-width: $bp-pc)
  .boxt
    height: 51vw
    // padding-bottom: 7.5vw
  .deco
    display: flex
    justify-content: center
    height: 100%
  .title
    margin-bottom: 1vw
  .content
    font-size: 100vw * 22 / 1920

  .bird
    right: 8.5vw
    top: 230px
    width: 5vw
@media screen and (max-width: $bp-mb)
  .boxt
    margin: 18vw 8vw 0

  .deco
    margin-bottom: 10vw

  .title
    margin-bottom: 5vw
    font-size: 23px

  .content
    font-size: 100vw * 13 / 375
  .bird
    right: -5vw
    bottom: -1vw
    width: 20vw
// dot
.dot10
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot10
    margin-bottom: 2vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot10
    margin-bottom: 12vw

// --------------------------------
// tree
.tree
  position: absolute
  z-index: 3

@media screen and (min-width: $bp-pc)
  .t2
    width: 9vw
    bottom: 8vw
    right: 11vw
  .t3
    width: 12vw
    bottom: 12vw
    right: -4vw

@media screen and (max-width: $bp-mb)
  .t2
    width: 44vw
    top: -12vw
    right: -32vw

// butterfly
.butt
  position: absolute

@media screen and (min-width: $bp-pc)
  .butt
    right: 11vw
    bottom: 7vw
    width: 3vw
@media screen and (max-width: $bp-mb)
  .butt
    right: 24vw
    top: -9vw
    width: 12vw

// single pic
.single
  width: 100%
  height: 100%
  position: relative
  background:
    image: url(./S10/1.png)
    size: cover
    position: center
.text_en
  position: absolute
  img
    height: 100%

@media screen and (min-width: $bp-pc)
  .text_en
    height: 33vw
    left: -3vw
    top: 13vw
@media screen and (max-width: $bp-mb)
  .single
    height: 150vw
    background-position: 70% center
  .text_en
    height: 90vw
    left: 4vw
    bottom: 22vw
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
