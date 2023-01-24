<template>
  <div class="container">
    <h1>Joke Gnenerator</h1>
    <p class="joke">{{ joke }}</p>
    <button @click="getJoke">Next Joke</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "component",
  data() {
    return {
      joke: "",
    };
  },
  methods: {
    async getJoke() {
      try {
        const response = await axios.get("https://icanhazdadjoke.com", {
          headers: { Accept: "application/json" },
        });
        this.joke = response.data.joke;
      } catch (error) {
        console.error(error);
      }
    },
  },
  created() {
    this.getJoke();
  },
};
</script>

<style></style>
