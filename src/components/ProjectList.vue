<template>
    <div class="container">
        <div class="header">
            <div>
                <img class="icon" src="../assets/megaphone.png">
                모집중인 프로젝트
            </div>
            <img class="arrow" src="../assets/chevron.png" >
        </div>
        <ProjectVue
            v-for="project in projects"
            :key="project.id"
            :title="project.title"
            :tags="project.tags"
            :hashTags="project.hashTags"
            :isHearted="project.isHearted"
            :content="project.content"
            :likes="project.likes"
        />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ProjectVue from './ProjectVue.vue';

export default defineComponent({
  name: 'ProjectList',
  components: {
    ProjectVue
  },
  data() {
    return {
      msg: "BeVelop",
      projects: [
        {
          id: 1,
          tags: ['사이드 프로젝트', '라이프스타일'],
          title: '사용자 개선 프로젝트 함께 하실 분 찾아요!',
          hashTags: ['#기획자', '#UI디자이너'],
          isHearted: false,
          content: '현재 사이드 프로젝트 진행중에 있으며 초기 아이디어 구상은 끝낸 상태입니다. 많이 지원해주세요!!',
          likes: 10
        },
        {
          id: 2,
          tags: ['스타트업', '라이프스타일'],
          title: '힙한 인테리어 소품으로 생활을 즐겁게!',
          hashTags: ['#백엔드', '#풀스택'],
          isHearted: true,
          content: '집안을 힙하게 꾸며주는 다양한 아이템을 판매하는 서비스를 함께 만들어갈 백엔드 개발자 구해요!',
          likes: 30
        }
      ]
    }
  }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   .container {
     display: flex;
     flex-direction: column;
     align-items: center;

     width: 100%;
     height: auto;

     font-size: 21px;
     font-family: 'Pretendard';
   }

   .header {
     display: flex;
     justify-content: space-between;
     align-items: center;

     width: 340px;
     height: 50px;

     padding: 20px 10px 10px;

     font-size: 18px;
     font-weight: 600;
     font-family: 'Pretendard';
   }

   .header > div {
    display: flex;
    align-items: center;

    height: 50px;
   }

   .icon {
    width: 20px;
    height: 20px;
    padding-right: 5px;
   }

   .arrow {
    width: 24px;
    height: 24px;
    transform: rotate(-90deg);
    transform-origin: center;
   }
  </style>
  