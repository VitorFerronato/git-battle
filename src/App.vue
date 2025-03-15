<template>
  <div id="app">
    <div class="image-box">
      <img src="./assets/wallpapper.png" alt="" />
    </div>

    <div class="input-container">
      <div class="input-box">
        <GBInput label="User 1" />
        <span>VS</span>
        <GBInput label="User 2" />
      </div>
    </div>

    <div class="button-box">
      <GBButton />
    </div>
  </div>
</template>

<script setup>
import GBInput from "./components/GBInput.vue";
import GBButton from "./components/GBButton.vue";
</script>

<style scoped>
#app {
  width: 100vw;
  height: 100vh;
  background-color: var(--bg-color);
}

.image-box {
  display: flex;
  justify-content: center;
  padding-top: 2rem;
}

.image-box img {
  width: 300px;
}

.input-container {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin-top: 2rem;
}

.input-container .input-box {
  display: flex;
  align-items: center;
  gap: 4rem;
}

.input-box span {
  color: var(--white-color);
  margin-top: 3rem;
}

.button-box {
  position: relative;
  display: flex;
  justify-content: center;
  margin-top: 2rem;
}
</style>
