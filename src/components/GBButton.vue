<template>
  <button v-bind="$attrs" type="submit">
    <div class="button">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      {{ title }}
    </div>
  </button>
</template>

<script setup>
defineProps({ title: String });
</script>

<style scoped>
button {
  all: unset;
  position: relative;
  transition: 0.3s;
  cursor: pointer;
}

.button {
  position: absolute;
  top: calc(50% + 3rem);
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 12px 24px;
  color: var(--primary-color);
  text-transform: uppercase;
  text-decoration: none;
  letter-spacing: 5px;
  font-size: 16px;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
  overflow: hidden;
  transition: 0.2s;
}

button:hover {
  transform: scale(1.1);
}

.button::before {
  content: "";
  position: absolute;
  top: 2px;
  left: 2px;
  bottom: 2px;
  width: 50%;
}

.button span:nth-child(1) {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(
    to right,
    var(--secondary-color),
    var(--primary-color)
  );
  animation: animate1 2s linear infinite;
  animation-delay: 1s;
}

@keyframes animate1 {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

.button span:nth-child(2) {
  position: absolute;
  top: 0;
  right: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(
    to bottom,
    var(--secondary-color),
    var(--primary-color)
  );
  animation: animate2 2s linear infinite;
  animation-delay: 2s;
}

@keyframes animate2 {
  0% {
    transform: translateY(-100%);
  }
  100% {
    transform: translateY(100%);
  }
}

.button span:nth-child(3) {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(
    to left,
    var(--secondary-color),
    var(--primary-color)
  );
  animation: animate3 2s linear infinite;
  animation-delay: 1s;
}

@keyframes animate3 {
  0% {
    transform: translateX(100%);
  }
  100% {
    transform: translateX(-100%);
  }
}

.button span:nth-child(4) {
  position: absolute;
  top: 0;
  left: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(
    to top,
    var(--secondary-color),
    var(--primary-color)
  );
  animation: animate4 2s linear infinite;
  animation-delay: 2s;
}

@keyframes animate4 {
  0% {
    transform: translateY(100%);
  }
  100% {
    transform: translateY(-100%);
  }
}
</style>
