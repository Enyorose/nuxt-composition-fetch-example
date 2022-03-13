<template>
  <div>
    <app-header>
      <h1 class="text-5xl md:text-6xl xl:text-7xl font-bold m-6">
        Experiments with Data Fetching
      </h1>
      <p class="text:lg md:text-xl max-w-prose">
        This repo demonstrates the different ways that you can fetch data in
        NuxtJS
      </p>
      <AppButton :link="cta" />
    </app-header>
  </div>
</template>

<script setup>
const cta = {
  url: "dogs",
  text: "API in Action",
};
</script>
