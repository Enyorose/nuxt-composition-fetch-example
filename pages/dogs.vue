<template>
  <div>
    <AppCard />
    <section class="container my-8 mx-2">
      <h2 class="text-3xl font-semibold">List of Dog Breeds</h2>
      <ul class="ml-4">
        <li v-for="breed in breedList" :key="breed.id">
          {{ breed }}
        </li>
      </ul>
    </section>
  </div>
</template>
<script>
import {
  defineComponent,
  ref,
  useFetch,
  useContext,
} from "@nuxtjs/composition-api";
export default defineComponent({
  setup() {
    const { $axios } = useContext();
    const breedList = ref("");
    const { fetch, fetchState } = useFetch(async () => {
      const response = await $axios.$get("https://dog.ceo/api/breeds/list/all");
      breedList.value = await Object.keys(response.message);
      console.log(fetchState);
    });
    fetch();

    return {
      breedList,
    };
  },
});
</script>
