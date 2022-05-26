<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="text" placeholder="Search Jokes...">
    <input type="submit" value="Search Jokes">
  </form>
</template>

// the component for the search box 

<script>
export default {
  name: "SearchJokes",
  data() {
    return {
      text: ""
    };
  },
  methods: {
    onSubmit() {
      this.$emit("search-text", this.text);
      this.text = "";
    }
  }
};
</script>

// this.text = ""; empties the search text box again

<style>
</style>