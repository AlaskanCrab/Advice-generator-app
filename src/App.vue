<template>
  <main>
    <div class="container">
      <div class="middle-content">
        <h1 v-for="advice in adviceApi">ADVICE #{{ advice.id }}</h1>
        <p v-for="advice in adviceApi">"{{ advice.advice }}"</p>

        <img
          class="img-line"
          src="./images/pattern-divider-desktop.svg"
          alt=""
        />
        <button @click="refresh" class="dice-btn">
          <img class="img-dice" src="./images/icon-dice.svg" alt="" />
        </button>
      </div>
    </div>
    <div class="attribution">
      Challenge by
      <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
        >Frontend Mentor</a
      >. Coded by
      <a href="https://github.com/AlaskanCrab" target="_blank">AlaskanCrab</a>.
    </div>
  </main>
</template>

<script setup>
import { ref, onMounted } from "vue";

const adviceApi = ref([]);

const getAdvice = async () => {
  return fetch("https://api.adviceslip.com/advice").then((response) =>
    response.json()
  );
};
onMounted(() => {
  getAdvice().then((data) => {
    adviceApi.value = data;
  });
});

const refresh = () => {
  window.location.reload();
};
</script>
