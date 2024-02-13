<template>
    <div >{{ msg }}
      <img src="../assets/chevron.png" />
      <img src="../assets/mypage.png" />
      <img src="../assets/alarm.png" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HeaderVue',
  data() {
    return {
      msg: "BeVelop"
    }
  }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   div {
     display: flex;
     justify-content: space-evenly;
     align-items: center;

     width: 100%;
     height: 48px;

     font-size: 22px;
     font-family: 'Pretendard';
     border: 1px solid black;
   }

   div > img:nth-child(1){
    margin-right: 150px;
   }
  </style>
  