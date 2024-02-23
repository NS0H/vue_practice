<template>
    <ProfileImage></ProfileImage>
    <ProfileForm @formSubmitted="updateProfile" />
    <ProfileDisplay v-if="profile" :profile="profile" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import ProfileImage from "../components/ProfileImage.vue";
import ProfileForm from '../components/ProfileForm.vue';
import ProfileDisplay from '../components/ProfileDisplay.vue';

interface Profile {
    name: string;
    des: string; 
    role: string;
    object: string;
    tech: string;
}

export default defineComponent({
    name: 'MyPage',
    components: {
    ProfileImage,
    ProfileForm,
    ProfileDisplay
  },
  setup() {
    const profile = ref<Profile | null>(null);

    function updateProfile(updatedProfile: Profile) {
      profile.value = updatedProfile;
    }

    return {
      profile,
      updateProfile,
    };
  },
});
</script>

<style lang="scss" scoped>
    .my-page {
        width: 360px;
    }
</style>