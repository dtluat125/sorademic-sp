<template>
  <div class="app-wrapper">
    <div class="app">
      <AppBar />
      <router-view />
    </div>
  </div>
</template>

<script lang="ts" setup>
import AppBar from "@/components/AppBar.vue";
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro&display=swap");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

* {
  margin: 0;
  vertical-align: middle;
}

.app-wrapper {
  width: 100%;
  .app {
    margin: 0 auto;
    position: relative;
    background: #f5f5f9;
    min-height: 100vh;
  }
  font-family: "Be Vietnam Pro", sans-serif;
}
</style>
