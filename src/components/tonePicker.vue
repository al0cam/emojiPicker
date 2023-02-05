<script setup lang="ts">
import { defineProps } from "vue";

const props = defineProps<{
  emoji: string;
}>();

const tones = [
  {
    name: "Light Tone",
    value: "&#x1F3FB;",
  },
  {
    name: "Medium Light Tone",
    value: "&#x1F3FC;",
  },
  {
    name: "Medium Tone",
    value: "&#x1F3FD;",
  },
  {
    name: "Medium Dark Tone",
    value: "&#x1F3FE;",
  },
  {
    name: "Dark Tone",
    value: "&#x1F3FF;",
  },
];
</script>

<template>
  <div id="tonePickerContainer">
    <div id="emojiVanilla">
      <span v-html="emoji" title="Vanilla Tone"></span>
    </div>
    <div id="emojiTones">
      <span
        v-for="tone in tones"
        :key="tone.name"
        :title="tone.name"
        v-html="emoji + tone.value"
      ></span>
    </div>
  </div>
</template>

<style scoped>
#tonePickerContainer {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}
</style>
