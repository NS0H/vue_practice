<template>
    <div class="container">
        <div class="header">
            <div>
                <img class="icon" src="../assets/hot.png">
                <red>HOT</red>한 포스트
            </div>
            <img class="arrow" src="../assets/chevron.png" >
        </div>
        <PostVue
            v-for="post in posts"
            :key="post.id"
            :id="post.id"
            :imgSrc="post.imgSrc"
            :title="post.title"
            :views="post.views"
            :hashTags="post.hashTags"
            :isMarked="post.isMarked"
            :content="post.content"
        />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import PostVue from './PostVue.vue';

export default defineComponent({
  name: 'ProjectList',
  components: {
    PostVue
  },
  data() {
    return {
      msg: "BeVelop",
      posts: [
        {
            id : 1,
            imgSrc : "../assets/banner1.png",
            title: "감정일기 플랫폼 '데일리'",
            views : 117,
            hashTags: ['#JAVA', '#Spring'],
            isMarked: false,
            content: "이제는 정신 건강 관리에 대한 중요성이 높아지고..."
        },
        {
            id : 2,
            imgSrc : "../assets/banner2.png",
            title: "감정일기 플랫폼 '데일리'",
            views : 117,
            hashTags: ['#JAVA', '#Spring'],
            isMarked: false,
            content: "이제는 정신 건강 관리에 대한 중요성이 높아지고..."
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

   red {
    color: red;
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
  