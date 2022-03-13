<template>
  <article>
    <h3 class="text-3xl font-semibold m-4 md:m-6">Title Here</h3>
    <img :src="images" />
  </article>
</template>
<script>
export default {
  data() {
    return {
      images: [],
    };
  },
  async fetch() {
    this.images = await fetch("https://dog.ceo/api/breeds/image/random/")
      .then((res) => res.json())
      .then((data) => data.message);
  },
};
</script>
