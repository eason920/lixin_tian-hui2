<template>
  <div
    data-aos-once="false"
    data-aos="fade-in"
    data-aos-duration="1000"
    data-aos-delay="0"
  >
    <img class="tree" src="./all/tree2.png" />
  </div>
</template>

<style lang='sass' scoped>
@import "src/assets/style/myvar"

%treeAni
  animation: tree 4s infinite alternate
  transform: skewX(-2deg)
  transform-origin: 50% 100%
  @keyframes tree
    to
      transform: skewX(2deg)
.tree
  width: 100%
  @extend %treeAni
</style>
