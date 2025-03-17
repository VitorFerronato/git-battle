<template>
  <div
    class="tooltip"
    @mouseover="showTooltip = true"
    @mouseleave="showTooltip = false"
  >
    <span>i</span>

    <Transition name="fade">
      <div v-if="showTooltip" class="tooltip-baloon">
        <span class="font-weight-bold title">How we calculate the winner?</span>
        <span class="subtitle"
          ><span class="font-weight-bold">Followers:</span> 2 points</span
        >
        <span class="subtitle"
          ><span class="font-weight-bold">Public Repos:</span> 1.5 points</span
        >
        <span class="subtitle"
          ><span class="font-weight-bold">Stars:</span> 2 points</span
        >
        <span class="subtitle"
          ><span class="font-weight-bold">Forks:</span> 1 points</span
        >
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref } from "vue";
const showTooltip = ref(false);
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.title {
  font-size: 14px;
  margin-bottom: 0.5rem;
}

.subtitle {
  font-size: 12px;
}

.font-weight-bold {
  font-weight: bold;
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
  right: -14rem;
  top: calc(50% + 2rem);
  transform: translateY(-50%);

  display: flex;
  flex-direction: column;
  border: 1px solid var(--primary-color);
  background-color: var(--bg-color);
  padding: 8px;
  border-radius: 4px;
  width: 200px;
  color: var(--white-color);
}
</style>
