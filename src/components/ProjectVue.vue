<template>
    <div class="project">
        <div class="tags">
            <p
                class="tag"
                v-for="tag in tags" 
                :key="tag">
                {{ tag }}
            </p>
        </div>
        <div class="title">{{ title }}</div>
        <div class="hashTags">
            <p
                class="hashTag"
                v-for="hashTag in hashTags" 
                :key="hashTag">
                {{ hashTag }}
            </p>
        </div>
        <div class="content">{{ content }}</div>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';

export default defineComponent({
  name: 'ProjectVue',
  props: {
    tags: Array as PropType<string[]>,
    title: String,
    hashTags: Array as PropType<string[]>,
    isHearted: Boolean,
    content: String,
    likes: Number
  },
  data() {
    return {
      msg: "BeVelop"
    }
  }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   .project {
     display: flex;
     flex-direction: column;
     align-items: flex-start;

     width: 320px;
     height: 180px;
     padding: 10px;

     font-size: 21px;
     font-family: 'Pretendard';
     border: 1px solid #EEEEEE;
     border-radius: 5px;
   }

   .tags {
    display: flex;
    flex-direction: row;

    font-family: Pretendard;
    font-size: 14px;
    font-weight: 400;
   }

   .title {
    color: #000;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;
   }

   .hashTags {
    display: flex;
    flex-direction: row;

    color: #8B95A1;
    font-family: Pretendard;
    font-size: 13px;
    font-weight: 400;
   }

   .content {
    color: #6B7684;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;
   }
  </style>
  