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
<script>
  export default {
    name: 'MenuBar',
    // props: {
    //   msg: String
    // },
    data () {
      return {
        menuList : ['홈', '팀원구인', '포스트']
      }
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
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
  