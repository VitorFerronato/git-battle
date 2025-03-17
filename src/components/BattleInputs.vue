<template>
  <form @submit.prevent="compareUsers" class="battle-container">
    <div>
      <div class="image-box">
        <img src="../assets/wallpapper.png" alt="" />
      </div>
      <div class="input-container">
        <div class="input-box">
          <GBInput v-model="user1" label="User 1" />
          <img src="../assets/vs-showdown.png" alt="" class="showdown" />
          <GBInput v-model="user2" label="User 2" />
        </div>
      </div>

      <div class="button-box">
        <GBButton v-if="!isLoading" title="Fight!" type="submit" />
        <GBLoader v-else />
      </div>
    </div>
  </form>
</template>

<script setup>
import { ref } from "vue";
import GBInput from "./GBInput.vue";
import GBButton from "./GBButton.vue";
import GBLoader from "./GBLoader.vue";
import { toast } from "vue3-toastify";
import "vue3-toastify/dist/index.css";
defineProps({
  results: Object,
});

const emits = defineEmits(["update:results"]);

const user1 = ref("");
const user2 = ref("");
const isLoading = ref(false);

const compareUsers = async () => {
  isLoading.value = true;

  if (!user1.value || !user2.value) {
    showToastBar("Insert two users");
    isLoading.value = false;
    return;
  }

  if (user1.value == user2.value) {
    showToastBar("Insert two different users");
    isLoading.value = false;
    return;
  }

  try {
    const response = await fetch(
      `http://127.0.0.1:5000/compare?dev1=${user1.value}&dev2=${user2.value}`
    );

    if (response.status == 200) {
      const data = await response.json();
      emits("update:results", data);
    } else showToastBar("Please, insert two users");
  } catch (error) {
    console.log("Error fetching data:", error);
    showToastBar("Error fetching data. Please try again");
  }

  isLoading.value = false;
};

const showToastBar = (text) => {
  toast(text, {
    theme: "auto",
    type: "error",
    position: "bottom-right",
    autoClose: 2000,
    pauseOnHover: false,
    dangerouslyHTMLString: true,
  });
};
</script>

<style scoped>
.battle-container {
  display: flex;
  justify-content: center;
  height: 100vh;
}

.image-box {
  display: flex;
  justify-content: center;
  padding-top: 1rem;
}

.image-box img {
  width: 350px;
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
  align-items: center;
}

.showdown {
  width: 100px;
}
</style>
