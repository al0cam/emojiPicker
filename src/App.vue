<script setup lang="ts">
import EmojiItem from "./components/emojiItem.vue";
import TonePicker from "./components/tonePicker.vue";
const pray = "&#x1F64F;";
</script>

<template>
  <EmojiItem />

  <TonePicker :emoji="pray" />
</template>

<style scoped>
header {
  line-height: 1.5;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }
}
</style>
