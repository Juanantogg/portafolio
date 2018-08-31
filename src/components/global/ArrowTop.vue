<template lang="pug">
  .arrow-top
    div(@click='moveToTop')
      small: slot
      span &utrif;
</template>

<script>
export default {
  name: 'arrow-top',
  methods: {
    moveToTop () {
      this.$emit('moveToTop')
    }
  }
}
</script>

<style lang="scss" scoped>
.arrow-top {
  width: 100%;
  position: absolute;
  top: 0;
  display: flex;
  justify-content: center;
  div {
    // background-color: #ff0;
    width: 5em;
    display: flex;
    align-items: center;
    flex-direction: column;
    position: relative;
    cursor: pointer;
    &:hover small {
      text-decoration: underline;
    }
  }
  small {
    position: relative;
    top: 0px;
    color: rgb(0, 0, 0);
  }
  span {
    position: relative;
    font-size: 2.5em;
    top: -20px;
    animation: arrowTop 1s infinite;
  }
}
@keyframes arrowTop {
  0% {
    top: -20px;
  }
  35% {
    top: 0;
  }
  75% {
    top: 0;
  }
  100% {
    top: -20px;
  }
}
</style>
