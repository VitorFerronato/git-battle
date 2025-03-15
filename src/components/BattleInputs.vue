<template>
  <div>
    <div class="image-box">
      <img src="../assets/wallpapper.png" alt="" />
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
</template>

<script setup>
import { ref } from "vue";
import GBInput from "./GBInput.vue";
import GBButton from "./GBButton.vue";
import GBLoader from "./GBLoader.vue";

defineProps({
  results: Object,
});

const emits = defineEmits(["update:results"]);

const user1 = ref("");
const user2 = ref("");
const isLoading = ref(false);

const compareUsers = async () => {
  emits("update:results", {
    dev1: {
      avatar: "https://avatars.githubusercontent.com/u/1024025?v=4",
      followers: 229248,
      public_repos: 8,
      score: 900773.0,
      total_forks: 56115,
      total_stars: 193075,
      username: "torvalds",
      winner: true,
    },
    dev2: {
      avatar: "https://avatars.githubusercontent.com/u/810438?v=4",
      followers: 88859,
      public_repos: 282,
      score: 181374.0,
      total_forks: 155,
      total_stars: 1539,
      username: "gaearon",
      winner: false,
    },
    winner: "torvalds",
  });

  // isLoading.value = true;

  // if (!user1.value || !user2.value) {
  //   alert("Por favor, insira dois usuários!");
  //   isLoading.value = false;
  //   return;
  // }

  // try {
  //   const response = await fetch(
  //     `http://127.0.0.1:5000/compare?dev1=${user1.value}&dev2=${user2.value}`
  //   );

  //   if (response.status == 200) results.value = await response.json();
  //   else alert("Erro ao buscar os dados, Tente novamente!");
  // } catch (error) {
  //   console.log("Erro ao buscar dados:", error);
  //   alert("Erro ao buscar os dados. Tente novamente!");
  // }

  // isLoading.value = false;
};
</script>

<style scoped>
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

.button-box {
  display: flex;
  justify-content: center;
  margin: 2.5rem 0 6rem 0;
}
</style>
