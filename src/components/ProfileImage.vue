<template>
  <div 
    class="background"
    :style="{ backgroundImage: 'url(' + backgroundImageUrl + ')' }">
    <label 
      v-if="currentView === 'form'" 
      for="backgroundImage" 
      class="btn_back">
      + 배경 이미지 수정하기
    </label>
    <input 
      id="backgroundImage"
      type="file" 
      @change="handleBackgroundImageChange" 
      accept="image/*"
      hidden />
  </div>
  <div class="profile">
    <div 
      class="img_profile"
      :style="{ backgroundImage: 'url(' + profileImageUrl + ')' }">
    </div>
    <label 
      v-if="currentView === 'form'" 
      for="profileImage" 
      class="btn_profile">
      +
    </label>
    <input 
      id="profileImage"
      type="file" 
      @change="handleProfileImageChange" 
      accept="image/*"
      hidden />
  </div>
</template>


<script lang="ts">
import { defineComponent, ref} from 'vue';

export default defineComponent({
  name: 'ProfileImage',
  props: {
    currentView: String
  },
  setup() {
    const profileImageUrl = ref('');
    const backgroundImageUrl = ref('');
    
    const handleProfileImageChange = (event: Event) => {
      const files = (event.target as HTMLInputElement).files;
      if (files && files[0]) {
        const fileReader = new FileReader();
        fileReader.onload = (e) => {
          if (e.target && e.target.result) {
            profileImageUrl.value = e.target.result as string;
          }
        };
        fileReader.readAsDataURL(files[0]);
      }
    };

    const handleBackgroundImageChange = (event: Event) => {
      const files = (event.target as HTMLInputElement).files;
      if (files && files[0]) {
        const fileReader = new FileReader();
        fileReader.onload = (e) => {
          if (e.target && e.target.result) {
            backgroundImageUrl.value = e.target.result as string;
          }
        };
        fileReader.readAsDataURL(files[0]);
      }
    };

    return {
      profileImageUrl,
      backgroundImageUrl,
      handleProfileImageChange,
      handleBackgroundImageChange
    };
  }
});
</script>
  

<style lang="scss" scoped>
.background {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  width: 360px;
  height: 117px;

  background-color: black;
  background-size: cover;
  background-position: center;
  border-radius: 0px 0px 58.5px 0px;
}

.btn_back {
  background: none;
  border: none;
  padding: 20px;

  color: #FFF;
  font-family: Pretendard;
  font-size: 16px;
  font-weight: 500;
}

.img_profile {
  width: 100px;
  height: 100px;
  background-color: #F2F4F6;
  border-radius: 100px;
  border: 3px solid #FFF;
  background-size: cover;
  background-position: center;

  position: absolute;
  top: 90px;
  left: 24px;   
}

.btn_profile {
  width: 30px;
  height: 30px;
  text-align: center;

  font-size: 27px;
  font-weight: 100;
  color: #FFFFFF;
  background-color: #8B95A1;
  border: none;
  border-radius: 20px;

  position: absolute;
  top: 160px;
  left: 100px;
}

label:hover {
  cursor: pointer;
}
</style>
