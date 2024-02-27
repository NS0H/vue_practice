<template>
    <div class="profile-display">
        <div class="personal">
          <div>
            <div class="name">{{ profile.name }}</div>
            <button class="re_btn" @click="editProfile">프로필 수정 ></button>
          </div>
          <div class="description">{{ profile.des }}</div>
        </div>
        <p class="hr"></p>
        <div>
            <div class="label">프로필</div>
            <div class="profile">
                <div>{{ profile.role }}</div>
                <div>{{ profile.object }}</div>
            </div>
            <div class="label">포트폴리오</div>
            <div class="result pdf">{{ profile.pdf?.name || '파일 없음' }}</div>
            <div class="result">{{ profile.link }}</div>
            <div class="label">기술스택</div>
            <div class="result">{{ profile.tech }}</div>
        </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, PropType } from 'vue';
  
  export default defineComponent({
    name: 'ProfileDisplay',
    props: {
      profile: {
        type: Object as PropType<{ 
          name: string;
          des: string;
          role: string;
          object: string;
          pdf: File | null;
          link: string;
          tech: string;
        }>,
        required: true,
      },
    },
    setup(props, { emit }) {
    function editProfile() {
      emit('showForm'); 
    }

    return { editProfile };
  }
  });
  </script>
  
  <style lang="scss" scoped>
  .profile-display {
    display: flex;
    flex-direction: column;

    width: 360px;
    padding-top: 48px;
  }

  .profile-display > div {
    padding-left: 20px;
    width: 320px;
  }

  .personal > div:first-child {
    display: flex;
    justify-content: space-between;
  }

  .name {
    color: #000;
    font-family: Pretendard;
    font-size: 24px;
    font-weight: 600;

    padding-bottom: 13px;
  }

  .re_btn {
    border: none;
    color: #8B95A1;
    background-color: #FFFFFF;
    text-align: right;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;
  }

  .re_btn:hover {
    cursor: pointer;
  }

  .description {
    width: 320px;
    height: 76px;
    word-wrap: break-word;
    
    color: #000;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 400;
  }

  .hr {
    width: 360px;
    height: 2px;
    background-color: #F2F4F6;
  }

  .label {
    color: #000;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;

    margin-top: 34px;
    margin-bottom: 18px;
  }

  .profile {
    display: flex;
    width: 100%;
    height: 48px;
    justify-content: space-between;
  }

  .profile div {
    width: 136px;
    padding-left: 20px;
    display: flex;
    align-items: center;

    color: #404A5C;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;

    border-radius: 6px;
    border: 1px solid #DADEE2;
    background: #FFF;
  }

  .result {
    width: 320px;
    height: 48px;
    padding-left: 20px;
    display: flex;
    align-items: center;

    border-radius: 6px;
    border: 1px solid #DADEE2;
    background: #FFF;

    color: #404A5C;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;
  }

  .pdf {
    margin-bottom: 12px;
  }
  </style>
