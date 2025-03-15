<template>
  <div>
    <div class="winner">
      <h4>WINNER</h4>
      <p>{{ winner }}</p>
    </div>

    <div class="button">
      <GBButton title="Return" @click="$emit('cleanResults')" />
    </div>
  </div>
</template>

<script setup>
import GBButton from "./GBButton.vue";

defineProps({
  winner: String,
});
</script>

<style scoped>
.winner {
  margin-top: 4rem;
  border: 0.5px solid var(--primary-color);
  width: 250px;
  padding: 1rem;
  color: var(--white-color);
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
</style>
