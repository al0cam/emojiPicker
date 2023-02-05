<script setup lang="ts">
import { defineProps, ref } from "vue";

const props = defineProps<{
  emoji: {
    name: string;
    value: string;
  };
}>();

const tones = [
  {
    name: "Vanilla Tone",
    value: "",
  },
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

function pickTone(emoji: string) {
  return function (tone: string) {
    return emoji + tone;
  };
}
const pickToneForEmoji = pickTone(props.emoji.value);

const toneContainerHidden = ref(true);
</script>

<template>
  <div id="toneContainer" v-if="!toneContainerHidden">
    <span
      v-for="tone in tones"
      :key="tone.name"
      :title="emoji.name + ' ' + tone.name"
      v-html="pickToneForEmoji(tone.value)"
    >
    </span>
  </div>
  <h1>
    <span
      v-html="emoji.value"
      :title="emoji.name"
      @click="toneContainerHidden = !toneContainerHidden"
    ></span>
  </h1>
</template>

<style scoped>
toneContainer {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  place-items: center;
  place-content: center;
}
</style>
