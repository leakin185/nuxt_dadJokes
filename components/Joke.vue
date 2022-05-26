<template>
  <nuxt-link :to="'jokes/' + id">
    <div class="joke">
      <p>{{ joke }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Joke",
  props: ["joke", "id"]
};
</script>

// props need to be specified when you are using the component, refer to Jokes/index.vue

<style>
.joke {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>