<template lang="pug">
  .about.min-height(:class='{"about-down": aboutMe === 1}')
    ArrowTop(@moveToTop='changeToHeader')
      slot Inicio
    h3.subtitle Sobre mí
</template>

<script>
import ArrowTop from '@/components/global/ArrowTop'

export default {
  name: 'about',
  components: {
    ArrowTop
  },
  methods: {
    changeToHeader () {
      this.$emit('showHeader')
    }
  },
  props: ['aboutMe']
}
</script>

<style lang="scss" scoped>
.about {
  background-color: teal;
  position: absolute;
  top: 0;
  z-index: 1;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
  transition: top linear .4s;
}
.about-down {
  top: 100vh;
}
</style>
