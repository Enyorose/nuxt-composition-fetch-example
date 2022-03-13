<template>
  <div>
    <AppCard />
    <ul>
      <li v-for="dog in dogs" :key="dog.id">
        {{ dog }}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      dogs: [],
      images: [],
    };
  },

  async fetch() {
    this.dogs = await fetch("https://dog.ceo/api/breeds/list/all")
      .then((res) => res.json())
      .then((data) => Object.keys(data.message));
  },
};
</script>
