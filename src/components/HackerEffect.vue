<template>
  <h1 data-value="SKANN">SKANN</h1>
</template>

<script>
export default {
  mounted() {
    const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    let iterations = 0;

    const interval = setInterval(() => {
      const h1 = document.querySelector("h1");
      h1.innerText = h1.innerText
        .split("")
        .map((letter, index) => {
          if (index < iterations) {
            return h1.dataset.value[index];
          }
          return letters[Math.floor(Math.random() * 26)];
        })
        .join("");
      iterations += 1 / 5;
      if (iterations >= h1.dataset.value.length) clearInterval(interval);
    }, 40);
  },
};
</script>

<style>
body {
  background-color: black;
}
h1 {
  color: white;
  font-size: 5rem;
  font-family: "Space Mono", monospace;
}
</style>
