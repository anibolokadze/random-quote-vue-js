<template>
  <main>
    <Quotes />
  </main>
</template>

<script>
import Quotes from "./components/Quotes";
export default {
  name: "App",
  components: {
    Quotes,
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-shadow: border-box;
  font-family: "Manrope", sans-serif;
}
:root {
  --LightCyan: hsl(193, 38%, 86%);
  --Neon-Green: hsl(150, 100%, 66%);
  --Grayish-Blue: hsl(217, 19%, 38%);
  --Dark-Grayish-Blue: hsl(217, 19%, 24%);
  --Dark-Blue: hsl(218, 23%, 16%);
}
main {
  background: var(--Dark-Blue);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
