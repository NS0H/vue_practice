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
    pdf: File | null;
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
    const currentView = ref('form');
    const profile = ref({ 
        name: '',
        des: '',
        role: '',
        object: '',
        pdf: null,
        link: '',
        tech: '',
    });

    function showForm() {
      currentView.value = 'form';
    }

    function showDisplay(updatedProfile: Profile) {
      Object.assign(profile.value, updatedProfile);
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