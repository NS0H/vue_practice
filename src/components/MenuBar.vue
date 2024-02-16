<template>
    <div class="container">
      <div 
        v-for="menu in menuList"
        :key="menu"
        :name="menu">
        {{ menu }}
      </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'MenuBar',
  setup() {
    const menuList = ref(['홈', '팀원구인', '포스트']);

    return {
      menuList
    };
  }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   .container {
     display: flex;
     justify-content: space-around;
     align-items: center;

     width: 100%;
     height: 42px;

     font-size: 16px;
     color: gray;
     font-family: 'Pretendard';
   }

   .container > div {
    width: 120px;
    text-align: center;
   }

   .container > div:nth-child(1) {
    color: black;
   }
  </style>
  