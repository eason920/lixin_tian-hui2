<template>
  <div
    data-aos-once="false"
    data-aos="fade-in"
    data-aos-delay="0"
    data-aos-duration="1400"
  >
<div class="butterfly02">
<div class="butterfly1">
  <img src="./S1/00.png" class="imgbg">
  <img src="./S1/butterfly20.png" class="fly2">
  <img src="./S1/butterfly20.png" class="fly1">
  <img src="./S1/3.png" class="fly5">
</div>
</div>
  </div>
</template>

<style lang='sass' scoped>
  .imgbg 
    width: 100%
  @keyframes an 
    to
      transform: translateX(0%)
  .butterfly02
    transform: scaleX(-1)rotate(50deg)
    width: 100%

  .butterfly1
    transform: translateY(50%)
    animation: an 3s linear infinite alternate
  .fly1,.fly2
    position: absolute
    top: 0
    left: 0
    width: 100%
    transform-origin: 100% 100%
    animation: an 1s alternate ease-in-out infinite
  .fly1
    transform: scaleX(0.8)
  .fly2
    transform: scaleX(1.1)
  .fly5
    position: absolute
    top: 40%
    left: 98%
    width: 17%
</style>
