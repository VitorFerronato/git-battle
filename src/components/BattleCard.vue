<template>
  <div class="result-container">
    <div class="result-user-info">
      <ResultCard :dev="results?.dev1" />
      <img src="./assets/vs-showdown.png" alt="" class="showdown" />
      <ResultCard :dev="results?.dev2" />
    </div>

    <div v-if="results?.winner">
      <div class="winner">
        <h4>WINNER</h4>
        <p>{{ results.winner }}</p>

        <div
          class="tooltip"
          @mouseover="showTooltip = true"
          @mouseleave="showTooltip = false"
        >
          <span>i</span>

          <!-- Adicionando a transição -->
          <Transition name="fade">
            <div v-if="showTooltip" class="tooltip-baloon">
              <span class="font-weight-bold">Como calculamos o vencedor?</span>
              <span
                ><span class="font-weight-bold">Followers:</span> 2 Pontos</span
              >
              <span
                ><span class="font-weight-bold">Public Repos:</span> 1.5
                Pontos</span
              >
              <span><span class="font-weight-bold">Stars:</span> 2 Pontos</span>
              <span><span class="font-weight-bold">Forks:</span> 1 Pontos</span>
            </div>
          </Transition>
        </div>
      </div>

      <div class="button">
        <GBButton title="Return" @click="$emit('resetBattle')" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import ResultCard from "./ResultCard.vue";
import GBButton from "./GBButton.vue";

const showTooltip = ref(false);
defineProps({
  results: Object,
});
</script>

<style scoped>
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

.winner {
  position: relative;
  margin-top: 2rem;
  border: 0.5px solid var(--primary-color);
  width: 250px;
  padding: 1rem;
  color: var(--white-color);
}

.tooltip {
  width: 30px;
  position: absolute;
  right: -3rem;
  top: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  transform: translateY(-50%);
  border: 1px solid var(--primary-color);
  border-radius: 50%;
  cursor: pointer;
}

.tooltip-baloon {
  position: absolute;
  right: -11rem;
  top: 50%;
  transform: translateY(-50%);
  border: 1px solid var(--primary-color);
  background-color: var(--bg-color);
  padding: 8px;
  border-radius: 4px;
  width: 200px;
  color: var(--white-color);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.winner h4 {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: -2rem;
  background-color: var(--bg-color);
}

.winner p {
  margin-top: 0.5rem;
  padding: 0;
  text-align: center;
  font-size: 24px;
}

.button {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

.how-winner {
  margin-top: 5rem;
  color: var(--white-color);
}

.how-winner:hover {
  text-decoration: underline;
}

.font-weight-bold {
  font-weight: bold;
}
</style>
