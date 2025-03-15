<template>
  <div class="result-card">
    <div class="image"><img :src="dev?.avatar" /></div>
    <h3>{{ dev.username }}</h3>
    <div class="item-card">
      <div class="item-text">
        <p>Followers</p>
        <p class="result-text">{{ dev.followers }}</p>
      </div>
    </div>

    <div class="item-card">
      <div class="item-text">
        <p>Public Repos</p>
        <p class="result-text">{{ dev.public_repos }}</p>
      </div>
    </div>

    <div class="item-card">
      <div class="item-text">
        <p>Forks</p>
        <p class="result-text">{{ dev.total_forks }}</p>
      </div>
    </div>

    <div class="item-card">
      <div class="item-text">
        <p>Stars</p>
        <p class="result-text">{{ dev.total_stars }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  dev: Object,
});
</script>

<style scoped>
.result-card {
  width: 500px;

  display: flex;
  flex-direction: column;
  gap: 1rem;

  border: 0.5px solid var(--primary-color);
  border-radius: 10px;
  padding: 1rem 2rem;

  color: var(--white-color);
}

.image {
  display: flex;
  justify-content: center;
}

.image img {
  width: 80px;
  border-radius: 50%;
  margin-top: -4rem;
}

h3 {
  text-align: center;
  color: var(--white-color);
}

.item-card {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}

.item-text {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.result-text {
  font-size: 20px;
  font-weight: 600;
}
</style>
