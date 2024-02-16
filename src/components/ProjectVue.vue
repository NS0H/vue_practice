<template>
    <div class="project">
        <div class="tags">
            <p
                class="tag"
                v-for="tag in tags" 
                :key="tag"
                :class="tagColor(tag)">
                {{ tag }}
            </p>
        </div>
        <div class="title">{{ title }}</div>
        <div class="hashTags">
            <div
                class="hashTag"
                v-for="hashTag in hashTags" 
                :key="hashTag">
                {{ hashTag }}
            </div>
        </div>
        <div class="content">{{ content }}</div>
        <img 
            class="heart"
            @click="heartChange"
            :src="heartImagePath"
         />
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType, computed} from 'vue';

export default defineComponent({
  name: 'ProjectVue',
  props: {
    id: Number,
    tags: Array as PropType<string[]>,
    title: String,
    hashTags: Array as PropType<string[]>,
    isHearted: Boolean,
    content: String
  },
  emits: ['change-heart-status'],
  setup(props, { emit }) {
    const tagColor = (tag: string) => {
      if (tag.includes('사이드 프로젝트')) {
        return 'purple';
      } else if (tag.includes('라이프스타일')) {
        return 'black';
      } else if (tag.includes('스타트업')) {
        return 'pink';
      } else {
        return 'default';
      }
    };

    const heartChange = () => {
      emit('change-heart-status', props.isHearted, props.id);
      console.log(props.isHearted, props.id);
    };

    const heartImagePath = computed(() => {
      return props.isHearted
        ? require('../assets/heart_fill.png')
        : require('../assets/heart_blank.png');
    });

    return {
      tagColor,
      heartChange,
      heartImagePath
    };
  }
});
</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style lang="scss" scoped>
   .project {
    position: relative;
     display: flex;
     flex-direction: column;
     align-items: flex-start;

     width: 320px;
     height: 180px;
     padding: 10px;

     font-size: 21px;
     font-family: 'Pretendard';
     border: 1px solid #EEEEEE;
     border-radius: 5px;
   }

   .tags {
    display: flex;
    flex-direction: row;
    gap: 10px;
    margin-bottom: 10px;

    font-family: Pretendard;
    font-size: 14px;
    font-weight: 400;

    color: #fff;
   }

   .tag {
    display: flex;
    padding: 3px 8px;
    justify-content: center;
    align-items: center;

    border-radius: 4px;
   }

   .purple {
    background-color: #7A5DF5;
   }

   .black {
    background-color: #1F1F1F;
   }

   .pink {
    background-color: #FF26A8;
   }

   .title {
    color: #000;
    font-family: Pretendard;
    font-size: 16px;
    font-weight: 500;
   }

   .hashTags {
    display: flex;
    flex-direction: row;

    color: #8B95A1;
    font-family: Pretendard;
    font-size: 13px;
    font-weight: 400;

    margin: 2px 0px 25px;
   }

   .content {
    color: #6B7684;
    font-family: Pretendard;
    font-size: 14px;
    font-weight: 400;

    padding-right: 20px;
   }

   .heart {
    width: 24px;
    height: 24px;

    position: absolute;
    right: 5%;
   }

   .heart:hover {
    cursor: pointer;
   }
  </style>
  