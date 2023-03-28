<template>
  <div class="wrapper">
    <p>Quote</p>

    <div v-if="loading" class="loading">Searching...</div>

    <div v-if="quote.error">
      <p>{{ quote.error }}</p>
    </div>

    <div>
      <h1>{{ quote.content }}</h1>
    </div>

    <div class="divider"></div>

    <button @click="getRandomQuote">
      <img src="../assets/icon-dice.svg" />
    </button>
  </div>
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

<style scoped>
.wrapper {
  background: var(--Dark-Grayish-Blue);
  width: 80%;
  height: 300px;
  border-radius: 20px;
  color: var(--LightCyan);
  padding: 20px;
}
p {
  color: var(--Neon-Green);
}
h1 {
  font-size: 20px;
}
button {
  all: unset;
}
.divider {
  background-image: url("../assets/pattern-divider-mobile.svg");
  background-repeat: no-repeat;
  background-size: cover;
  height: 20px;
}
</style>
