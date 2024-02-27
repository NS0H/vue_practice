<template>
    <div class="profile_form">
      <form>
        <div>
          <label>닉네임</label>
          <input 
            v-model="profile.name" 
            :class="{'highlight': profile.name}"
            id="name" 
            type="text">
            <div v-if="showNameMessage" class="pop_text">
              사용 가능한 닉네임입니다.
            </div>
        </div>
        <div>
            <label >한줄소개</label>
            <textarea 
              v-model="profile.des"
              :class="{'highlight': profile.des}" 
              id="des">
            </textarea>
        </div>
        <div>
          <label>프로필</label>
          <div class="profile_select">
            <select v-model="profile.role" :class="{'highlight': profile.role}" id="role">
                <option value="" disabled selected>직무</option>
                <option value="UX Designer">UX Designer</option>
                <option value="UI Designer">UI Designer</option>
            </select>
            <select v-model="profile.object" :class="{'highlight': profile.object}" id="object">
                <option value="" disabled selected>관심분야</option>
              <option value="Service Design">서비스 디자인</option>
              <option value="Web Design">웹 디자인</option>
            </select>
          </div>
        </div>
        <div class="portfolio">
            <label>포트폴리오</label>
            <div class="file_upload"  :class="{ 'highlight': fileName }">
              <input 
                :class="{'highlight': profile.pdf}"
                id="pdf" 
                type="file" 
                @change="handleFileChange"
                hidden>
              <div class="file_name">{{ fileName ? fileName : '포트폴리오 첨부(PDF 권장)' }}</div>
              <label for="pdf" class="upload_btn">수정</label>
            </div>
              <input 
                v-model="profile.link" 
                :class="{'highlight': profile.link}"
                id="link" 
                type="text" 
                placeholder="링크/URL">
              <div v-if="showLinkMessage" class="pop_text">
                올바른 형식의 링크를 넣어주세요.
              </div>
        </div>
        <div class="techstack">
            <label>기술스택</label>
            <input v-model="profile.tech" id="tech" type="text" placeholder="기술 스택을 추가해보세요">
        </div>
        <button type="button" @click="submitForm">입력 완료</button>
      </form>
    </div>
</template>
  
<script lang="ts">
import { defineComponent, reactive, computed, ref} from 'vue';

interface Profile {
  name: string;
  des: string;
  role: string;
  object: string;
  pdf: File | null;
  link: string;
  tech: string;
}

export default defineComponent({
  name: 'ProfileForm',
  emits: {
    formSubmitted: null,
  },
  setup(props, { emit }) {
    const fileName = ref('');
    const profile = reactive<Profile>({
      name: '',
      des: '',
      role: '',
      object: '',
      pdf: null,
      link: '',
      tech: '',
    });

    const showNameMessage = computed(() => {
      return !profile.name.includes('a') && profile.name !== '';
    });

    const showLinkMessage = computed(() => {
      return !profile.link.includes('http') && !profile.link.includes('www') && profile.link !== '' ;
    });

    function handleFileChange(event: Event) {
      const inputElement = event.target as HTMLInputElement;
      const files = inputElement.files;
      if (files && files[0]) {
        profile.pdf = files[0];
        fileName.value = files[0].name;
      }
    }

    function submitForm() {
      emit('formSubmitted', profile);
    }

    return {
      profile,
      fileName,
      submitForm,
      showNameMessage,
      showLinkMessage,
      handleFileChange
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

.pop_text {
  margin-top: 8px;

  color: #7A5DF5;
  font-family: Pretendard;
  font-size: 12px;
  font-weight: 500;
}

label {
    color: #000;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;

    margin-bottom: 18px;
}

input, select, .file_upload {
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

    resize: none;
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

.portfolio input, .file_name {
    color: #404A5C;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;
    padding-left: 20px;
}

.portfolio input::placeholder {
  color: #404A5C;
}

.file_upload {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 12px;
}

.upload_btn {
  color: #8B95A1;
  text-align: right;
  font-family: Pretendard;
  font-size: 12px;
  font-weight: 500;

  margin-right: 20px;
  margin-bottom: 0px;
}

.techstack input {
    text-align: center;
    color: #404A5C;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 500;

    border: 1px dashed #8B95A1;
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

input:focus, textarea:focus, select:focus, .file_upload:focus {
  border: 1px solid #7A5DF5;
  outline: none;
}

.highlight {
  border: 1px solid #7A5DF5;
}

button, .upload_btn {
  cursor: pointer;
}
</style>