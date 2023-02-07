<script setup lang="ts">
import { ref } from "vue";

const props = defineProps<{
  emoji: {
    name: string;
    value: string;
  };
}>();

const currentEmoji = ref({
  name: props.emoji.name,
  value: props.emoji.value,
});

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
// TODO: highlight the current selected emoji and start the to the left and right from it
</script>

<template>
  <div>
    <div :id="'emoji' + emoji.name"></div>
    <div>
      <span
        v-html="currentEmoji.value"
        :title="currentEmoji.name"
        @click="toneContainerHidden = !toneContainerHidden"
        class="emoji"
      ></span>
    </div>
  </div>
  <Teleport :to="'#emoji' + emoji.name">
    <div id="toneContainer" v-if="!toneContainerHidden">
      <span
        v-for="tone in tones"
        :key="tone.name"
        :title="emoji.name + ' ' + tone.name"
        v-html="pickToneForEmoji(tone.value)"
        class="emoji"
        @click="
          currentEmoji.value = pickToneForEmoji(tone.value);
          currentEmoji.name = emoji.name + ' ' + tone.name;
          toneContainerHidden = true;
        "
      >
      </span>
    </div>
  </Teleport>
</template>

<style scoped>
.container {
  position: relative;
}
#toneContainer {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  place-items: center;
  place-content: center;
  background-color: #2e2e2e;
  border-radius: 0.5rem;
  position: absolute;
}

.emoji {
  font-size: 2rem;
  cursor: pointer;
}

.emoji:hover {
  color: #ffffff;
}
</style>
