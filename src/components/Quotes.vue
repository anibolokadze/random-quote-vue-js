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
        .get("https://api.quotable.io/random?maxLength=50")
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
  width: 300px;
  height: 200px;
  border-radius: 20px;
  color: var(--LightCyan);
  padding: 40px 20px;
  display: grid;
  position: relative;
}
p {
  color: var(--Neon-Green);
  text-align: center;
}
h1 {
  font-size: 20px;
  margin-block: 25px;
  text-align: center;
}
button {
  all: unset;
  position: absolute;
  top: 90%;
  left: 40%;
  background: var(--Neon-Green);
  height: 50px;
  width: 50px;
  padding: 10px;
  border-radius: 50%;
}
button:hover {
  cursor: pointer;
  box-shadow: 0 0 40px 0px var(--Neon-Green);
}
button img {
  margin: 13px;
}
.divider {
  background-image: url("../assets/pattern-divider-mobile.svg");
  background-repeat: no-repeat;
  height: 20px;
}

@media (min-width: 1000px) {
  .wrapper {
    width: 450px;
  }

  .divider {
    background-image: url("../assets/pattern-divider-desktop.svg");
    background-repeat: no-repeat;
    height: 20px;
  }
  button {
    left: 43%;
  }
}
</style>
