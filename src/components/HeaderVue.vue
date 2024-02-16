<template>
    <div >
      <router-link to="/">{{ msg }}</router-link>
      <img class="arrow" src="../assets/chevron.png" />
      <router-link to="/mypage"><img src="../assets/mypage.png" /></router-link>
      <img src="../assets/alarm.png" />
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'HeaderVue',
  setup() {
    const msg = ref("BeVelop");

    return {
      msg
    };
  }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   div {
     display: flex;
     justify-content: space-evenly;
     align-items: center;

     width: 360px;
     height: 48px;

     font-size: 22px;
     font-family: 'Pretendard';
     color: black;
     border: 1px solid black;
   }

   a {
     text-decoration: none;
     color: black;
   }

   .arrow{
    margin-right: 150px;
   }
  </style>
  