<template>
  <div class="relative">
    <section id="sec12">
      <div
        class="boxp"
        data-aos="fade-up"
        data-aos-duration="1000"
        data-aos-delay="0"
        data-aos-once="false"
      >
        <swiper v-if="hasSwiper" :options="swiperOptions12" ref="swipers12">
          <swiper-slide v-for="(item, i) in swipList" :key="'s12' + i">
            <div class="item">
              <div class="text">{{ item }}</div>
            </div>
          </swiper-slide>
          <template v-slot:button-prev>
            <div class="swiper-button-prev" @click="prevBtns12"></div>
          </template>
          <template v-slot:button-next>
            <div class="swiper-button-next" @click="nextBtns12"></div>
          </template>
          <template v-slot:pagination>
            <div class="swiper-pagination"></div>
          </template>
        </swiper>
        <div v-else class="single">
          <div class="text">外觀3D透視圖</div>
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
            樣品屋樣 品屋樣品
          </div>
          <div
            class="content"
            data-aos="fade-up"
            data-aos-duration="1000"
            data-aos-delay="0"
            data-aos-once="false"
          >
            XXXXXXXXXXXXXXXXXXX<br/>
            XXXXXXXXXXXXXXX<br/>
            XXXXXXXXXXXXXXXXXXXXXXX<br/>
            XXXXXXXXXXXXXXXXXXXXXXX
          </div>
          <tree2 class="tree t2" />
        </div>
        <ul class="dot12"
          v-if="hasSwiper"
          data-aos="fade-up"
          data-aos-duration="1000"
          data-aos-delay="0"
          data-aos-once="false"
        >
          <li
            v-for="item in 3"
            :key="'dot12' + item"
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
import tree2 from './tree2.vue'

export default {
  components: {
    Swiper,
    SwiperSlide,
    tree2,
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
        '樣品屋2',
        '樣品屋3',
        '樣品屋1',
      ],
      swiperOptions12: {
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
            if (eq >= 3) {
              eq = eq - 3
            }
            // console.log(eq) // 切換啟動前，告訴我現在是第幾個slide
            $('.dot12 li')
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
    prevBtns12() {
      this.$refs.swipers12.$swiper.slidePrev()
    },
    nextBtns12() {
      this.$refs.swipers12.$swiper.slideNext()
    },
    fnDotChange(i) {
      let eq = i - 1
      // console.log(eq)
      if (eq >= 3) {
        eq = eq - 3
      }
      // console.log(eq)
      this.$refs.swipers12.$swiper.slideTo(eq)
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
  &:nth-child(1), &:nth-child(4), &:nth-child(7)
    background-image: url('./S12/1.jpg')

  &:nth-child(2), &:nth-child(5), &:nth-child(8)
    background-image: url('./S12/2.jpg')

  &:nth-child(3), &:nth-child(6), &:nth-child(9)
    background-image: url('./S12/3.jpg')

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
#sec12
  overflow: hidden

.boxp

.boxt
  display: flex
  flex-direction: column

@media screen and (min-width: $bp-pc)
  #sec12
    overflow: hidden
    padding: 7vw 0
  .boxp // 47 + 8 = 55
    width: 60vw
    height: 33vw
    float: left
  .boxt // 100 - 55 = 45
    float: right
    width: 35vw
    padding:
      right: 8vw
    justify-content: flex-end
    height: 100%
    position: relative
@media screen and (max-width: $bp-mb)
  #sec12
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
    size: 1.59em
    weight: bold

.content
  color: #333
  line-height: 1.5
  text-align: justify

@media screen and (min-width: $bp-pc)
  .boxt
    height: 33vw
    padding
      right: 8vw
    position: relative
  .deco
    display: flex
    justify-content: flex-end
    height: 100%
  .title
    // margin-bottom: 1vw
    width: 0
    position: absolute
    right: 0vw
    top: 0vw
@media screen and (max-width: 1360px)  
  .boxt
    font:
      size: 14px
@media screen and (max-width: 980px)  
  .boxt
    height: 38vw
  .boxp
    height: 38vw

@media screen and (max-width: $bp-mb)
  .boxp
    height: auto
  .boxt
    margin: 18vw 8vw 0
    height: auto

  .deco
    margin-bottom: 10vw

  .title
    margin-bottom: 5vw
    font-size: 23px

  .content
    font-size: 100vw * 13 / 375

// dot
.dot12
  @include swiperCustomDot
@media screen and (min-width: $bp-pc)
  .dot12
    margin-bottom: 2vw
    // width: 100px
@media screen and (max-width: $bp-mb)
  .dot12
    margin-bottom: 12vw
    justify-content: flex-end

// --------------------------------
// tree
.tree
  position: absolute
  z-index: 3

@media screen and (min-width: $bp-pc)
  .t2
    width: 8vw
    bottom: 4vw
    right: -4vw
@media screen and (max-width: 960px)  
  .t2
    width: 8vw
    bottom: 0vw
    right: -4vw

@media screen and (max-width: $bp-mb)
  .t2
    width: 30vw
    bottom: -28vw
    left: -14vw

// single pic
.single
  width: 100%
  height: 100%
  position: relative
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
