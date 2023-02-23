<script setup>
import { toRefs } from 'vue';
import { RouterLink } from 'vue-router';

const props = defineProps({
  image: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  subtitle: {
    type: String,
    required: true,
  },
});

const { image, title, subtitle } = toRefs(props);
</script>

<template>
  <RouterLink to="library">
    <div
      class="bg-[#111111] p-4 rounded-md m-2 hover:bg-[#252525] cursor-pointer"
    >
      <img :src="image" class="rounded-md" alt="image of something" />
      <div class="text-white pt-4 font-semibold text-[17px]">{{ title }}</div>
      <div class="text-gray-400 pt-4 font-semibold text-[14px]">
        {{ subtitle }}
      </div>
    </div>
  </RouterLink>
</template>
