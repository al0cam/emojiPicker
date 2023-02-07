<script setup lang="ts">
import EmojiItem from "./components/emojiItem.vue";
const pray = {
  name: "Pray",
  value: "&#x1F64F;",
};
</script>

<template>
  <button><h1>ok</h1></button><br />
  <button><h1>ok</h1></button><br />
  <button><h1>ok</h1></button><br />
  <button><h1>ok</h1></button><br />
  <EmojiItem :emoji="pray" />
  <button><h1>ok</h1></button><br />
  <button><h1>ok</h1></button><br />
  <button><h1>ok</h1></button><br />
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
