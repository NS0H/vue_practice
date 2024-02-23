<template>
    <div class="profile_form">
      <form>
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
                <option value="role" disabled selected>직무</option>
                <option value="UX Designer">UX Designer</option>
                <option value="UI Designer">UI Designer</option>
              <!-- ... 추가 역할 -->
            </select>
            <select v-model="profile.object" id="object">
                <option value="object" disabled selected>관심분야</option>
              <option value="UX Designer">UX Designer</option>
              <option value="UI Designer">UI Designer</option>
              <!-- ... 추가 역할 -->
            </select>
          </div>
        </div>
        <div class="portfolio">
            <label for="portfolio">포트폴리오</label>
            <input v-model="profile.pdf" id="pdf" type="text" placeholder="포트폴리오 첨부(PDF 권장)">
            <input v-model="profile.link" id="link" type="text" placeholder="링크/URL">
        </div>
        <div class="techstack">
            <label for="techstack">기술스택</label>
            <input v-model="profile.tech" id="tech" type="text" placeholder="기술 스택을 추가해보세요">
        </div>
        <button type="button" @click="submitForm">입력 완료</button>
      </form>
    </div>
</template>
  
<script lang="ts">
import { defineComponent, reactive} from 'vue';

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
      des: '',
      role: 'role',
      object: 'object',
      pdf: '',
      link: '',
      tech: '',
    });

    function submitForm() {
      // 폼 제출 로직
      emit('formSubmitted', profile); // 메인 페이지로 변경할 컴포넌트와 프로필 데이터 전달
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
    padding-left: 20px;

    color: #404A5C;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;
}

.portfolio input {
    color: #404A5C;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;
    padding-left: 20px;
}

#pdf {
    margin-bottom: 12px;
}

.techstack input {
    text-align: center;
    color: #404A5C;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;
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

    margin-top: 27px;
}
</style>