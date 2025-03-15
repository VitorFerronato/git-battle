<template>
  <a v-bind="$attrs" href="#" class="button">
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    Fight!</a
  >
</template>

<style scoped>
a {
  position: absolute;
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

a:hover {
  transform: scale(1.1);
}

a::before {
  content: "";
  position: absolute;
  top: 2px;
  left: 2px;
  bottom: 2px;
  width: 50%;
}

a span:nth-child(1) {
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

a span:nth-child(2) {
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

a span:nth-child(3) {
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

a span:nth-child(4) {
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
