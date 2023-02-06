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
// TODO: consider inline emoji picker popup
// TODO: check bordercases of emoji picker when it is too far right
// TODO: add current emoji variable and define it in the picker on the left side
//       divided by a vertical line
</script>

<template>
  <Teleport :to="'#emoji' + emoji.name">
    <div id="toneContainer" v-if="!toneContainerHidden">
      <span
        v-for="tone in tones"
        :key="tone.name"
        :title="emoji.name + ' ' + tone.name"
        v-html="pickToneForEmoji(tone.value)"
      >
      </span>
    </div>
  </Teleport>

  <h1>
    <div :id="'emoji' + emoji.name">
      <span
        v-html="emoji.value"
        :title="emoji.name"
        @click="toneContainerHidden = !toneContainerHidden"
      ></span>
    </div>
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
