<template>
    <div class="container">
        <div id="main">
            사이드 프로젝트에서 <br />
            하나의 수입 수단까지
        </div>
        <div id="sub">스토리 자세히 보기 ></div>
        <div id="slide"></div>
        <div id="focus"></div>
    </div>
</template>
<script>
  export default {
    name: 'SlideVue',
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

   #sub {
    font-size: 12px;
    color: #494949;
    margin-top: -5px;
   }

   #slide {
    width: 168px;
    height: 2px;
    margin-top: 25px;

    background-color: black;
    opacity: 8%;
   }

   #focus {
    position: absolute;
    top: 245.5px;
    width: 56px;
    height: 2px;
    
    background-color: black;
   }
  </style>
  