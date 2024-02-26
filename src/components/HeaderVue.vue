<template>
    <div >
      <span class="page" @click="goToHome">{{ msg }}</span>
      <img class="arrow" src="../assets/chevron.png" />
      <img class="page" src="../assets/mypage.png" @click="goToMyPage" />
      <img src="../assets/alarm.png" />
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { useRouter } from 'vue-router';

export default defineComponent({
  name: 'HeaderVue',
  setup() {
    const router = useRouter();
    const msg = ref("BeVelop");

    function goToHome() {
      router.push('/');
    }

    function goToMyPage() {
      router.push('/mypage');
    }

    return {
      msg,
      goToHome,
      goToMyPage
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
   }

   .page:hover {
    cursor: pointer;
   }

   a {
     text-decoration: none;
     color: black;
   }

   .arrow{
    margin-right: 150px;
   }
  </style>
  