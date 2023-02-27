<script setup lang="ts">
import { ref } from "vue";

const props = defineProps<{
  emojiArray: string[];
  tone: string;
}>();
</script>

<template>
  <div>
    <span
      v-for="emojiWithTone in emojiArray.map((item) => {
        return item + tone;
      })"
      >{{ "  " + emojiWithTone }}</span
    >
  </div>
</template>

<style scoped></style>
