<template>
    <div class="profile_form">
      <form @submit.prevent="submitForm">
        <div>
          <label for="name">닉네임</label>
          <input v-model="profile.name" id="name" type="text">
        </div>
        <div>
            <label for="description">한줄소개</label>
            <textarea v-model="profile.des" id="des"></textarea>
        </div>
        <div>
          <label for="profile">프로필</label>
          <div class="profile_select">
            <select v-model="profile.role" id="role">
                <option value="role">직무</option>
                <option value="UX Designer">UX Designer</option>
                <option value="UI Designer">UI Designer</option>
              <!-- ... 추가 역할 -->
            </select>
            <select v-model="profile.object" id="object">
                <option value="object">관심분야</option>
              <option value="UX Designer">UX Designer</option>
              <option value="UI Designer">UI Designer</option>
              <!-- ... 추가 역할 -->
            </select>
          </div>
        </div>
        <div>
            <label for="portfolio">포트폴리오</label>
            <input v-model="profile.pdf" id="pdf" type="text">
            <input v-model="profile.link" id="link" type="text">
        </div>
        <div>
            <label for="techstack">기술스택</label>
            <input v-model="profile.tech" id="tech" type="text">
        </div>
        <button type="submit">입력 완료</button>
      </form>
    </div>
</template>
  
<script lang="ts">
import { defineComponent, reactive, toRaw } from 'vue';

interface Profile {
  name: string;
  des: string;
  role: string;
  object: string;
  pdf: string;
  link: string;
  tech: string;
}

export default defineComponent({
  name: 'ProfileForm',
  emits: {
    formSubmitted: null, // 검증 함수가 필요 없다면 null을 할당할 수 있습니다.
  },
  setup(props, { emit }) {
    const profile = reactive<Profile>({
      name: '',
      role: 'role',
      object: 'object',
      des: '',
      pdf: '',
      link: '',
      tech: '',
    });

    function submitForm() {
      // `toRaw`를 사용하여 반응성을 가진 `profile` 객체를 일반 객체로 변환합니다.
      emit('formSubmitted', toRaw(profile));
    }

    return {
      profile,
      submitForm,
    };
  },
});
</script>

<style lang="scss" scoped>
.profile_form {
    display: flex;

    width: 360px;
    padding-top: 33px;
}

.profile_form form {
    padding-left: 20px;
    width: 320px;
}
form > div {
    display: flex;
    flex-direction: column;

    margin: 21px auto;
}

label {
    color: #000;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;

    margin-bottom: 18px;
}

input, select {
    height: 48px;
    border-radius: 6px;
    border: 1px solid #DADEE2;
    background: #FFF;
}

textarea {
    height: 86px;
    border-radius: 6px;
    border: 1px solid #DADEE2;
    background: #FFF;
}

.profile_select {
    display: flex;
    width: 100%;
    justify-content: space-between;
}

.profile_select select {
    width: 156px;
}

#pdf {
    margin-bottom: 12px;
}

button {
    width: 320px;
    height: 54px;
    border-radius: 6px;
    background: #7A5DF5;
    border : none;

    color: #FFF;
    text-align: center;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;
}
</style>