<template>
    <HeaderVue></HeaderVue>
    <MenuBar></MenuBar>
    <SlideVue></SlideVue>
</template>

<script>
import HeaderVue from './components/HeaderVue.vue'
import MenuBar from './components/MenuBar.vue'
import SlideVue from './components/SlideVue.vue'

export default {
  name: 'App',
  components: {
    HeaderVue,
    MenuBar,
    SlideVue
  }
}
</script>

<style>
#app {
  margin: 0 auto;
  height: 100%;
  max-width: 360px;
  display: grid;
  place-items: center;
}
</style>
