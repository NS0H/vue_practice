<template>
    <div class="background">
      <button>
        + 배경 이미지 추가하기
      </button>
    </div>
    <div class="profile">
      <img src="../assets/profile_empty.png" />
      <button>
        +
      </button>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref} from 'vue';

export default defineComponent({
  name: 'ProfileImage',
  setup() {
    // const background = '../';
    const profile = ref('../assets/profile_empty.png');

    return {
    profile
   };
   }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
  .background {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    width: 360px;
    height: 117px;

    background-color: black;
    border-radius: 0px 0px 58.5px 0px;
  }

  .background > button {
    background: none;
    border: none;
    padding: 20px;

    color: #FFF;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;
  }

  button:hover {
    cursor: pointer;
  }

  .profile > img {
    width: 100px;
    height: 100px;

    position: absolute;
    top: 90px;
    left: 24px;   
  }

  .profile > button {
    width: 30px;
    height: 30px;

    font-size: 25px;
    font-weight: 100;
    color: #FFFFFF;
    background-color: #8B95A1;
    border: none;
    border-radius: 20px;

    position: absolute;
    top: 160px;
    left: 90px; 
  }
  </style>
  