<script setup lang="ts">
const pray = "&#x1F64F;";

const lightTone = "&#x1F3FB;";
const mediumLightTone = "&#x1F3FC;";
const mediumTone = "&#x1F3FD;";
const mediumDarkTone = "&#x1F3FE;";
const darkTone = "&#x1F3FF;";

function pickTone(emoji: string) {
  return function (tone: string) {
    return emoji + tone;
  };
}
</script>

<template>
  <h1>
    <span v-html="pray"></span>
    <span v-html="pickTone(pray)(lightTone)"></span>
    <span v-html="pickTone(pray)(mediumLightTone)"></span>
    <span v-html="pickTone(pray)(mediumTone)"></span>
    <span v-html="pickTone(pray)(mediumDarkTone)"></span>
    <span v-html="pickTone(pray)(darkTone)"></span>
  </h1>
</template>
