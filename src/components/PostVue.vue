<template>
    <div class="post">
        <img
            class="banner"
            :src=imgSrc
        />
        <div class="header">
            <div class="title">{{ title }}</div>
            <div class="views">조회수 {{ views }}</div>
        </div>
        <div class="content">{{ content }}</div>
        <div class="hashTags">
            <div
                class="hashTag"
                v-for="hashTag in hashTags" 
                :key="hashTag">
                {{ hashTag }}
            </div>
        </div>
        <img 
            class="mark"
            src="../assets/bookmark.png"
         />
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType} from 'vue';

export default defineComponent({
  name: 'PostVue',
  props: {
    id: Number,
    imgSrc: String,
    title: String,
    views: Number,
    hashTags: Array as PropType<string[]>,
    isMarked: Boolean,
    content: String
  }
});

</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   .post {
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    width: 320px;
    height: 293px;
    margin-bottom: 14px;

    font-size: 21px;
    font-family: 'Pretendard';
    border-radius: 6px;
    border: 1px solid #EEE;
    background: #FFF;
   }

   .banner {
    width: 320px;
    height: 183px;
    border-radius: 6px 6px 0px 0px;
   }

   .header {
    width: 288px;
    padding: 19px 15px 7px 17px;

    display: flex;
    justify-content: space-between;
   }

   .title {
    color: #000;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;
   }

   .views {
    color: #404A5C;
    font-family: Pretendard;
    font-size: 12px;
    font-weight: 400;
   }

   .hashTags {
    display: flex;
    flex-direction: row;

    color: #8B95A1;
    font-family: Pretendard;
    font-size: 13px;
    font-weight: 400;

    margin-left: 17px;
    margin-top: 12px;
   }

   .content {
    color: #6B7684;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 400;

    padding-right: 20px;
    margin-left: 17px;
   }

   .mark {
    width: 24px;
    height: 24px;

    position: absolute;
    top: 5%;
    right: 5%;
   }

   .mark:hover {
    cursor: pointer;
   }
  </style>
  