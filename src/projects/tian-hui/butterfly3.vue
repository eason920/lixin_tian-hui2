<template>
  <div
    data-aos-once="false"
    data-aos="fade-in"
    data-aos-delay="0"
    data-aos-duration="1400"
  >
    <div class="wavw">
      <img src="./S1/butterfly3.png" />
    </div>
  </div>
</template>

<style lang='sass' scoped>
  @keyframes aniWave
    0%
      transform: translateY(-2px) scaleX(.7)
    50%
      transform: translateY(2px) scaleX(1)
    100%
      transform: translateY(-2px) scaleX(.7)

  .wavw
    height: 100%
    width: 100%
    transform: translateY(-5px)
    animation: aniWave 3s infinite forwards
    img
      width: 100%
</style>
