<template>
  <div>
    <nuxt-link to="/jokes">Back To Jokes</nuxt-link>
    <h2>{{ joke }}</h2>
    <hr>
    <small>Joke ID: {{ $route.params.id }}</small>
  </div>
</template>

// comments
// you can access the specific joke with the joke ID at  e.g. http://localhost:3000/jokes/123
// this page shows the individual joke when it is being clicked on
// <nuxt-link to="/jokes">Back To Jokes</nuxt-link> links back to the other page
// having the sub _id folder allows us to go to a subpage by simply appending any number at the back of http://localhost:3000/jokes

<script>
import axios from "axios";

export default {
  data() {
    return {
      joke: {}
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };

    try {
      const res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );

      this.joke = res.data.joke;
    } catch (err) {
      console.log(err);
    }
  },
  head() {
    return {
      title: this.joke,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for corny dad jokes"
        }
      ]
    };
  }
};
</script>

<style>
</style>