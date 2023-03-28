<template>
  <h1>Quotes</h1>

  <div v-if="loading" class="loading">Searching...</div>

  <div v-if="quote.error">
    <p>{{ quote.error }}</p>
  </div>

  <div>{{ quote.content }}</div>
  <button @click="getRandomQuote">click</button>
</template>
<script>
import axios from "axios";

export default {
  name: "Quotes",
  data() {
    return {
      quote: "",
      loading: true,
      error: null,
    };
  },
  mounted() {
    this.getRandomQuote();
  },
  methods: {
    getRandomQuote() {
      axios
        .get("https://api.quotable.io/random/")
        .then((response) => {
          this.quote = response.data;
          this.loading = false;
        })
        .catch(() => {
          this.quote = {
            error: "Oops! Something went wrong. Please try again later.",
          };
        });
    },
  },
};
</script>
