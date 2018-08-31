<template lang="pug">
  .arrow-down
        div(@click='moveToDown')
          span &dtrif;
          small: slot
</template>

<script>
export default {
  name: 'arrow-down',
  methods: {
    moveToDown () {
      this.$emit('moveToDown')
    }
  }
}
</script>

<style lang="scss" scoped>
.arrow-down {
  width: 100%;
  position: absolute;
  bottom: 0;
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
    color: teal;
  }
  span {
    position: relative;
    font-size: 2.5em;
    top: -10px;
    animation: arrowDown 1s infinite;
  }
}
@keyframes arrowDown {
  0% {
    top: -10px;
  }
  35% {
    top: 10px;
  }
  75% {
    top: 10px;
  }
  100% {
    top: -10px;
  }
}
</style>
