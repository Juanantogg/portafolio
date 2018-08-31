<template lang='pug'>
  .navigation(:class='{"navigation-black": showMenu}')
    .main-container
      h2.logo JG

      .logo-menu(@click='toggleMenu')
        span.menu(:class='{"menu-close": showMenu}')

    .nav-container(:class='{"nav-container-extended": showMenu}')
      ul
        li: a(href="#")  ¿Quién soy?
        li: a(href="#")  Mis habilidades
        li: a(href="#")  ¿Qué hago?
        li: a(href="#")  Mi experiencia
        li: a(href="#")  ¿A dónde voy?
        li: a(href="#")  Contactame
</template>

<script>
export default {
  name: 'Naviagtion',
  data () {
    return {
      showMenu: false
    }
  },
  methods: {
    toggleMenu () {
      this.showMenu = !this.showMenu
    }
  }
}
</script>

<style lang='scss' scoped>
.navigation {
  width: 100%;
  padding: 16px 16px 0;
  background-color: rgba(0, 0, 0, 0);
  display: flex;
  justify-content: center;
  position: fixed;
  top: 0;
  z-index: 10;
  transition: background-color linear .4s;
}
.navigation-black {
  background-color: rgba(0, 0, 0, 0.9);
}
.main-container {
  background-color: #000;
  border-radius: 5px;
  width: 100%;
  height: 50px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.logo {
  color: #FFF;
}
.logo-menu {
  width: 50px;
  height: 50px;
  display: flex;
  background-color: transparent;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  cursor: pointer;
  transition: background-color linear .4s;
  @media (hover: hover) {
    &:hover {
      background-color: rgba(255, 255, 255, 0.1);;
    }
  }
}
.menu,
.menu::before,
.menu::after {
  content: '';
  display: flex;
  justify-content: center;
  align-items: center;
  width: 5px;
  height: 5px;
  border-radius: 3px;
  background-color: #fff;
  position: relative;
}
.menu::before,
.menu::after {
  // transition: top linear .1s 0s;
}
.menu::before{
  position: absolute;
  top: -12px;
}
.menu::after {
  position: absolute;
  top: 12px;
}
.menu-close {
  &::before,
  &::after {
    top: 0;
    width: 30px;
    transition: top linear .1s 0s,;
  }
  &::before {
    transform: rotate(45deg);
  }
  &::after {
    transform: rotate(-45deg);
  }
}

.nav-container {
  background-color: rgba(0, 0, 0, 0.9);
  opacity: 0;
  position: absolute;
  top: 66px;
  height: 0;
  width: 100%;
  overflow: hidden;
  padding: 0 16px;
  transition: height linear 0s .4s,
              padding linear 0s .4s,
              opacity linear .4s 0s;
  ul {
    height: 100%;
    height: calc(100vh - 98px);
    margin: 0;
    border-radius: 5px;
    padding: 48px 16px;
    list-style: none;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
  }
  a {
    text-decoration: none;
    font-size: 1.6em;
    font-weight: 500;
    color: #FFF;
  }
}
.nav-container-extended {
  opacity: 1;
  height: calc(100vh - 66px);
  padding: 16px;
  transition: height linear 0s 0s,
              padding linear 0s 0s,
              opacity linear .4s 0s;

}
</style>
