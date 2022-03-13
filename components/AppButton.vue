<template>
  <nuxt-link
    :to="link.url"
    class="bg-red-300 my-4 py-2 px-4 rounded-sm font-semibold"
  >
    {{ link.text }}</nuxt-link
  >
</template>

<script setup>
const props = defineProps({
  link: Object,
});
</script>
