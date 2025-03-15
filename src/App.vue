<template>
  <div id="app">
    <div v-if="!results">
      <div class="image-box">
        <img src="./assets/wallpapper.png" alt="" />
      </div>
      <div class="input-container">
        <div class="input-box">
          <GBInput
            v-model="user1"
            label="User 1"
            @keypress.enter="compareUsers"
          />
          <img src="./assets/vs-showdown.png" alt="" class="showdown" />
          <GBInput
            v-model="user2"
            label="User 2"
            @keypress.enter="compareUsers"
          />
        </div>
      </div>
      <div class="button-box">
        <GBButton v-if="!isLoading" title="Fight!" @click="compareUsers" />
        <GBLoader v-else />
      </div>
    </div>

    <div v-else class="result-container">
      <div class="result-user-info">
        <ResultCard :dev="results?.dev1" />
        <img src="./assets/vs-showdown.png" alt="" class="showdown" />
        <ResultCard :dev="results?.dev2" />
      </div>

      <WinnerCard :winner="results?.winner" @cleanResults="results = null" />
    </div>
  </div>
</template>

<script setup>
import GBInput from "./components/GBInput.vue";
import GBButton from "./components/GBButton.vue";

import { ref } from "vue";
import GBLoader from "./components/GBLoader.vue";
import ResultCard from "./components/ResultCard.vue";
import WinnerCard from "./components/WinnerCard.vue";

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
    console.log("response", response);
    results.value = await response.json();
  } catch (error) {
    console.log("caiu no catch");
    console.log("Erro ao buscar dados:", error);
    alert("Erro ao buscar os dados. Tente novamente!");
  }

  isLoading.value = false;
};
</script>

<style scoped>
#app {
  min-width: 100vw;
  min-height: 100vh;
  background-color: var(--bg-color);
}

.image-box {
  display: flex;
  justify-content: center;
  padding-top: 1rem;
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
  margin: 2.5rem 0 6rem 0;
}

.result-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.result-user-info {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}

.showdown {
  width: 100px;
}
</style>
