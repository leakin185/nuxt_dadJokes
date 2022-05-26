<template>
  <div>
    <SearchJokes v-on:search-text="searchText"/> 
    <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/>
  </div>
</template>

// <Joke v-for="joke in jokes" :key="joke.id" :id="joke.id" :joke="joke.joke"/> render each joke in jokes according to the defined component Joke
// use console.log() for understanding of the data structures and effective debugging
// each joke in jokes is a component 
// for v-for, need to specific a unique identifier in this case: the v-bind key is joke.id

<script>
import axios from "axios";
import Joke from "../../components/Joke";
import SearchJokes from "../../components/SearchJokes";

export default {
  components: {
    Joke,
    SearchJokes
  },
  data() {
    return {
      jokes: []
    };
  },
  // life cycle method: created(), make a request to the API with axios
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };

    try {
      const res = await axios.get("https://icanhazdadjoke.com/search", config);

      this.jokes = res.data.results;
    } catch (err) {
      console.log(err);
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "application/json"
        }
      };

      try {
        const res = await axios.get(
          `https://icanhazdadjoke.com/search?term=${text}`,
          config // search bar API
        );

        this.jokes = res.data.results;
      } catch (err) {
        console.log(err);
      }
    }
  },
  head() {
    return {
      title: "Dad Jokes",
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