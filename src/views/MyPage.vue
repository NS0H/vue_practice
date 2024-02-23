<template>
    <ProfileImage></ProfileImage>
    <ProfileForm v-if="currentView === 'form'" @formSubmitted="showDisplay" />
    <ProfileDisplay v-if="currentView === 'display'" :profile="profile" @showForm="showForm" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import ProfileImage from "../components/ProfileImage.vue";
import ProfileForm from '../components/ProfileForm.vue';
import ProfileDisplay from '../components/ProfileDisplay.vue';

interface Profile {
    name: string;
    role: string;
    object: string;
    des: string;
    pdf: string;
    tech: string;
    link: string;
}

export default defineComponent({
    name: 'MyPage',
    components: {
    ProfileImage,
    ProfileForm,
    ProfileDisplay
  },
  setup() {
    const currentView = ref('form'); // 'form' 또는 'display'
    const profile = ref({ 
        name: '',
        des: '',
        role: 'role',
        object: 'object',
        pdf: '',
        link: '',
        tech: '',
    });

    function showForm() {
      currentView.value = 'form';
    }

    function showDisplay(updatedProfile: Profile) {
      profile.value = updatedProfile; // ProfileForm에서 전달된 프로필 정보 업데이트
      currentView.value = 'display';
    }

    return { currentView, profile, showForm, showDisplay };
  },
});
</script>

<style lang="scss" scoped>
    .my-page {
        width: 360px;
    }
</style>