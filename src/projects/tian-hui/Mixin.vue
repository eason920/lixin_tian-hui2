<template>
  <div class="relative">
    <section id="sec">
      <div class="container">
        <div class="header">header</div>
        <div class="box red">red</div>
        <div class="box green">green</div>
        <div class="box blue">blue</div>
      </div>
    </section>
  </div>
</template>

<script>

import { isMobile, isTablet } from '@/utils'

export default {
  name: 'section1',

  data() {
    return {
      isMobile,
      isTablet
    }
  },

  methods: {},

  created() {},

  mounted() {},

  computed: {}
}
</script>

<style lang="sass" scoped></style>

<style scoped>
.container {

}

.box {
  padding: 10px;
  margin: 0 auto;
  text-align: center;
  width: 80%;
  height: 500px;
}

.header {
  position: sticky;
  top: 0;
  left: 0;
  background-color: rgba(0,0,0,.5)
}
.red {
  background-color: red;
}

.blue {
  background-color: blue;
  height: 300px;
}

.green {
  background-color: green;
}
</style>
