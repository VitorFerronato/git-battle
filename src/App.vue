<template>
  <div id="app">
    <div class="image-box">
      <img src="./assets/wallpapper.png" alt="" />
    </div>

    <div class="input-container">
      <div class="input-box">
        <GBInput v-model="user1" label="User 1" />
        <span>VS</span>
        <GBInput v-model="user2" label="User 2" />
      </div>
    </div>

    <div class="button-box">
      <GBButton v-if="!isLoading" @click="compareUsers" />
      <GBLoader v-else />
    </div>
  </div>
</template>

<script setup>
import GBInput from "./components/GBInput.vue";
import GBButton from "./components/GBButton.vue";

import { ref } from "vue";
import GBLoader from "./components/GBLoader.vue";

const user1 = ref("");
const user2 = ref("");
const results = ref(null);
const isLoading = ref(false);

const compareUsers = async () => {
  isLoading.value = true;

  if (!user1.value || !user2.value) alert("Por favor, insira dois usuarios!");

  try {
    const response = await fetch(
      `http://127.0.0.1:5000/compare?dev1=${user1.value}&dev2=${user2.value}`
    );

    results.value = await response.json();
  } catch (error) {
    console.log("Erro ao buscar dados:", error);
    alert("Erro ao buscar os dados. Tente novamente!");
  }

  isLoading.value = false;
};
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
  margin-top: 2.5rem;
}
</style>
