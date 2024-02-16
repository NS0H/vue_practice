<template>
    <div class="container">
        <div class="main">
            사이드 프로젝트에서 <br />
            하나의 수입 수단까지
        </div>
        <div class="sub">스토리 자세히 보기 ></div>
        <div class="slide">
          <div class="focus"></div>
        </div>
        
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'SlideVue',
  setup(){ }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   .container {
     display: flex;
     justify-content: center;
     flex-direction: column;
     align-items: flex-start;

     width: 100%;
     height: 206px;

     font-size: 21px;
     font-family: 'Pretendard';

     background-image: url('../assets/SlideImage.png');
   }

   .container > div {
    margin: 15px;
   }

   .sub {
    font-size: 12px;
    color: #494949;
    margin-top: -5px;
   }

   .slide {
    width: 168px;
    height: 2px;
    margin-top: 25px;

    background-color: rgb(0, 0, 0, 0.08);
   }

   .focus {
    width: 56px;
    height: 2px;
    
    background-color: black;
   }
  </style>
  