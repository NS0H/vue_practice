<template>
    <div >{{ msg }}
      <img src="../assets/chevron.png" />
      <img src="../assets/mypage.png" />
      <img src="../assets/alarm.png" />
    </div>
</template>
<script>
  export default {
    name: 'HeaderVue',
    // props: {
    //   msg: String
    // },
    data () {
      return {
        msg: "BeVelop"
      }
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
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
  