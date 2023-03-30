<template>
  <div
    data-aos-once="false"
    data-aos="fade-in"
    data-aos-delay="0"
    data-aos-duration="1400"
  >
    <div class="deco">
      <div class="wavw">
        <img src="./S1/butterfly2.png" />
      </div>
    </div>
  </div>
</template>

<style lang='sass' scoped>
  @keyframes aniWave
    to
      transform: translateY(-2px) scaleX(.7)

  .wavw
    height: 100%
    width: 100%
    transform: translateY(2px) scaleX(1)
    animation: aniWave 1s ease-in-out infinite alternate
    img
      width: 100%

  .deco
    transform: rotate(45deg)
</style>
