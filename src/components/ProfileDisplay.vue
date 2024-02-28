<template>
  <div class="profile-display">
    <!-- 닉네임과 한줄 소개 -->
    <div class="personal">
      <div>
        <div class="name">{{ profile.name }}</div>
        <button class="re_btn" @click="editProfile">프로필 수정 ></button>
      </div>
      <div class="description">{{ profile.des }}</div>
    </div>
    <p class="hr"></p>
    <!-- 그 외 입력 정보 -->
    <div>
      <div class="label">프로필</div>
      <div class="profile">
          <div>{{ profile.role || '직무' }}</div>
          <div>{{ profile.object || '관심분야' }}</div>
      </div>
      <div class="label">포트폴리오</div>
      <div class="result pdf">{{ profile.pdf?.name || '파일 없음' }}</div>
      <div class="result">{{ profile.link || '링크/URL' }}</div>
      <div class="label">기술스택</div>
      <div class="tech_list">
        <div 
          class="tech_item" 
          v-for="(tech, index) in profile.tech" 
          :key="index"
          :style="{ backgroundColor: techColors[tech] || 'grey' }">
          {{ tech }}
        </div>
      </div>
    </div>
  </div>
</template>


<script lang="ts">
import { defineComponent, PropType } from 'vue';
import techColorsData from '@/assets/techColors.json';

// 기술 스택 별 색상 저장 인터페이스
interface TechColors {
  [key: string]: string;
}

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
        tech: string[];
      }>,
      required: true,
    },
  },
  setup(props, { emit }) {
    // 기술 스택 별 색상 저장
    const techColors: TechColors = techColorsData;

    // ProfileForm으로 이동
    function editProfile() {
      emit('showForm'); 
    }

    return { editProfile, techColors };
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

// 닉네임과 프로필 수정 버튼을 감싸는 div
.personal > div:first-child {
  display: flex;
  justify-content: space-between;
}

// 닉네임
.name {
  color: #000;
  font-family: Pretendard;
  font-size: 24px;
  font-weight: 600;

  padding-bottom: 13px;
}

// 프로필 수정 버튼
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

// 한줄 소개
.description {
  width: 320px;
  height: 76px;
  word-wrap: break-word;
  
  color: #000;
  font-family: Pretendard;
  font-size: 16px;
  font-weight: 400;
}

// 수평선
.hr {
  width: 360px;
  height: 2px;
  background-color: #F2F4F6;
}

// 전체 label
.label {
  color: #000;
  font-family: Pretendard;
  font-size: 16px;
  font-weight: 500;

  margin-top: 34px;
  margin-bottom: 18px;
}

// 직무 및 관심 분야
.profile {
  display: flex;
  width: 100%;
  height: 48px;
  justify-content: space-between;
}

// 직무와 관심 분야 각각 div
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

// 포트폴리오와 링크
.result {
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

// 기술 스택
.tech_list {
  display: flex;
  align-items: center;
  height: auto;
  flex-wrap: wrap;
  padding: 0px;
  column-gap: 7px;
  row-gap: 12px;
  max-width: 100%;

  color: #404A5C;
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
</style>
