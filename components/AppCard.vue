<template>
  <article class="m-8">
    <h3 class="text-3xl font-semibold m-4 md:m-6">Dog Image</h3>
    <p v-if="!dogImage">Image Not loading</p>
    <img :src="dogImage" v-else class="w-1/5 object-cover" />
  </article>
</template>
<script>
import {
  defineComponent,
  ref,
  useFetch,
  useContext,
} from "@nuxtjs/composition-api";
export default defineComponent({
  // options api image fetch
  /*
  data() {
    return {
      images: [],
    };
  },
  async fetch() {
    this.images = await fetch("https://dog.ceo/api/breeds/image/random/")
      .then((res) => res.json())
      .then((data) => data.message);
  },*/
  // composition api image fetch
  setup() {
    const dogImage = ref("");
    const { $axios } = useContext();
    const { fetch } = useFetch(async () => {
      const response = await $axios.$get(
        "https://dog.ceo/api/breeds/image/random/"
      );
      dogImage.value = response.message;
    });
    fetch();
    return { dogImage };
  },
});
</script>
