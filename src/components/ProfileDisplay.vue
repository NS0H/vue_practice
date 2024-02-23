<template>
    <div class="profile-display">
      <h1>{{ profile.name }}</h1>
      <p>{{ profile.role }}</p>
      <p>{{ profile.object }}</p>
      <p>{{ profile.des }}</p>
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
            tech: string;
        }>,
        required: true,
      },
    },
  });
  </script>
  