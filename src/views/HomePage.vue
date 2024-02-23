<template>
    <MenuBar></MenuBar>
    <SlideVue></SlideVue>
    <ProjectList></ProjectList>
    <PostList></PostList>
</template>

<script lang="ts">
import MenuBar from '../components/MenuBar.vue';
import SlideVue from '../components/SlideVue.vue';
import ProjectList from '../components/ProjectList.vue';
import PostList from '../components/PostList.vue';
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'HomePage',
    components: {
    MenuBar,
    SlideVue,
    ProjectList,
    PostList
  }
})
</script>



<!--
  App.vue에서는 라우터 만들어 주시면
  이제 router-view를 통해서 라우팅되는 페이지가 렌더링 되는 형태로 될꺼라 
  새로운 프로젝트를 생성하는게 아니라 라우터쪽 공부하시면서 작업해주시면 될꺼같구요 
  전체적으로 optionals API로 작업 해주셨던데 
  composition API 참고하셔서 작업해주신거 수정 해봐주시면 좋을것같습니다 
-->