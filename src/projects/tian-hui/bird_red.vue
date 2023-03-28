<template>
  <div
    data-aos-once="false"
    data-aos="fade-in"
    data-aos-duration="1000"
    data-aos-delay="0"
  >
    <img class="bird" src="./all/bird_red.png" />
  </div>
</template>

<style lang='sass' scoped>
@import "src/assets/style/myvar"

@keyframes bird
  to
    transform: skewX(2deg)
.bird
  width: 100%
  animation: bird 2s infinite alternate
  transform: skewX(-2deg)
  transform-origin: 50% 50%
</style>
