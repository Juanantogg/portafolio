<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: 'Roboto', sans-serif;
  overflow-x: hidden;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

h1,h2,h4,h5,h6 {
  font-family: 'Kaushan Script', serif;
  margin: 0;
}

.min-height {
  height: 100vh;
  min-height: 546px;
  width: 100%;
}
</style>
