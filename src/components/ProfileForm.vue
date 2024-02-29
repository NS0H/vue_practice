<template>
  <div class="profile_form">
    <form>
      <!-- 이름 입력 -->
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
      <!-- 한줄 소개 -->
      <div>
        <label >한줄소개</label>
        <textarea 
          v-model="profile.des"
          :class="{'highlight': profile.des}"
          id="des">
        </textarea>
      </div>
      <!-- 직무 및 관심 분야 -->
      <div>
        <label>프로필</label>
        <div class="profile_select">
          <select v-model="profile.role" :class="{'highlight': profile.role}" id="role">
              <option value="" disabled selected>직무</option>
              <option value="UX 디자이너">UX 디자이너</option>
              <option value="UI 디자이너">UI 디자이너</option>
          </select>
          <select v-model="profile.object" :class="{'highlight': profile.object}" id="object">
              <option value="" disabled selected>관심분야</option>
            <option value="서비스 디자인">서비스 디자인</option>
            <option value="웹 디자인">웹 디자인</option>
          </select>
        </div>
      </div>
      <!-- 포트폴리오 및 링크 -->
      <div class="portfolio">
        <label>포트폴리오</label>
        <!-- 파일 업로드 -->
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
        <!-- 릴크 첨부 -->
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
      <!-- 기술 스택 -->
      <div class="techstack">
          <label>기술스택</label>
          <div class="tech_container">
            <button class="add_tech" type="button" @click="addTech">
              +
            </button>
            <!-- 기술 스택 추가 후 사용되는 div -->
            <div v-if="profile.tech.length > 0" class="tech_list">
              <div 
                class="tech_item" 
                v-for="(tech, index) in profile.tech" 
                :key="index"
                :style="{ backgroundColor: techColors[tech] || 'grey' }">
                {{ tech }}
              </div>
            </div>
            <!-- 기술 스택 추가 전 사용되는 div -->
            <div v-else class="tech_none">
              기술 스택을 추가해보세요.
            </div>
          </div>
      </div>
      <button type="button" @click="submitForm">입력 완료</button>
    </form>
  </div>
</template>


<script lang="ts">
import { defineComponent, reactive, computed, ref} from 'vue';
import techColorsData from '@/assets/techColors.json';

// 입력 값 저장 인터페이스
interface Profile {
  name: string;
  des: string;
  role: string;
  object: string;
  pdf: File | null;
  link: string;
  tech: string[];
}

// 기술 스택 json값 저장 인터페이스
interface TechColors {
  [key: string]: string;
}

export default defineComponent({
  name: 'ProfileForm',
  emits: {
    formSubmitted: null,
  },
  setup(props, { emit }) {
    const newTech = ref(''); // 새로 추가된 기술 스택
    const fileName = ref(''); // 포트폴리오 파일 이름
    const profile = reactive<Profile>({
      name: '',
      des: '',
      role: '',
      object: '',
      pdf: null,
      link: '',
      tech: [],
    });

    // 기술 스택 별 색상 저장 데이터
    const techColors: TechColors = techColorsData;

    // 닉네임 확인
    const showNameMessage = computed(() => {
      return !profile.name.includes('a') && profile.name !== '';
    });

    //링크 형식 확인
    const showLinkMessage = computed(() => {
      return !profile.link.includes('http') && !profile.link.includes('www') && profile.link !== '' ;
    });

    // 기술 스택 추가 window prompt
    const addTech = () => {
      const newTech = window.prompt("추가할 기술스택을 입력하세요:");

      if (newTech !== null && newTech.trim() !== "") {
        profile.tech.push(newTech.trim());
      }
    };

    // 포트폴리오 파일 추가 함수
    function handleFileChange(event: Event) {
      const inputElement = event.target as HTMLInputElement;
      const files = inputElement.files;
      if (files && files[0]) {
        profile.pdf = files[0];
        fileName.value = files[0].name;
      }
    }

    // ProfileDisplay로 이동
    function submitForm() {
      emit('formSubmitted', profile);
    }

    return {
      profile,
      fileName,
      techColors,
      newTech,
      addTech,
      showNameMessage,
      showLinkMessage,
      handleFileChange,
      submitForm,
    };
  },
});
</script>


<style lang="scss" scoped>
// 전체 프로필 폼 스타일
.profile_form {
  display: flex;

  width: 360px;
  padding-top: 33px;
}

.profile_form form {
  padding-left: 20px;
  width: 320px;
}

// 각 label과 input을 감싸는 div
form > div {
  display: flex;
  flex-direction: column;

  margin: 21px auto;
}

// if문 통해서 나타나는 문구
.pop_text {
  margin-top: 8px;

  color: #7A5DF5;
  font-family: Pretendard;
  font-size: 12px;
  font-weight: 500;
}

// 전체 label
label {
  color: #000;
  font-family: Pretendard;
  font-size: 16px;
  font-weight: 500;

  margin-bottom: 18px;
}

// 전체적인 input 스타일
input, select, .file_upload {
    height: 48px;
    border-radius: 6px;
    border: 1px solid #DADEE2;
    background: #FFF;
}

// 한줄 소개
textarea {
    height: 86px;
    border-radius: 6px;
    border: 1px solid #DADEE2;
    background: #FFF;

    resize: none;
}

// 직무, 관심분야 선택
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

// 포트폴리오 및 링크
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

// 기술 스택
.tech_container {
  display: flex;
  justify-content: space-between;
}

.add_tech {
  display: inline-flex;
  height: 37px;
  padding: 10px 27px;
  justify-content: center;
  align-items: center;
  gap: 10px;

  border: none;
  border-radius: 6px;
  background: #F2F4F6;
  color: #505967;
  font-size: 25px;
  font-weight: 100;
}

.tech_list, .tech_none {
  width: 235px;
  padding: 9px 0px;
  text-align: center;

  color: #8B95A1;
  font-family: Pretendard;
  font-size: 14px;
  font-weight: 500;
  border-radius: 6px;
  border: 1px dashed #8B95A1;
}

.tech_list {
  display: flex;
  align-items: center;
  height: auto;
  flex-wrap: wrap;
  padding: 0px;
  column-gap: 7px;
  row-gap: 12px;

  border: none;
}

.tech_item {
  display: inline-flex;
  padding: 10px 27px;
  justify-content: center;
  align-items: center;

  color: #FFF;
  border-radius: 6px;
  color: #FFF;
  font-family: Pretendard;
  font-size: 14px;
  font-weight: 500;
}

// 입력 완료 버튼
form > button {
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

// 입력 중 스타일
input:focus, textarea:focus, select:focus, .file_upload:focus {
  border: 1px solid #7A5DF5;
  outline: none;
}

// 입력 후 스타일
.highlight {
  border: 1px solid #7A5DF5;
}

// 버튼 커서 스타일
button, .upload_btn {
  cursor: pointer;
}
</style>