<template>
    <HeaderVue></HeaderVue>
    <MenuBar></MenuBar>
    <SlideVue></SlideVue>
    <ProjectList></ProjectList>
</template>

<script setup lang="ts">
import HeaderVue from './components/HeaderVue.vue';
import MenuBar from './components/MenuBar.vue';
import SlideVue from './components/SlideVue.vue';
import ProjectList from './components/ProjectList.vue';
</script>

<style lang="scss">
#app {
  margin: 0 auto;
  height: 100%;
  max-width: 360px;
  display: grid;
  place-items: center;
}
</style>


<!-- 
router 셋팅해서 페이지 메인페이지도 라우팅 해보시는것을 권장 드립니다.

그외에 아직 로직컬 부분은 없어보여서 작업하실때 이부분만 우선적으로 고려해서 작업 해봐주시면 좋을것같습니다
-->