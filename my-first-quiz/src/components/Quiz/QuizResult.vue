<script setup>
import { useQuizStore } from "../../stores/QuizStore";
let QuizStore = useQuizStore();
</script>
<template>
  <div
    class="p-10 text-2xl font-semibold text-center text-white py-15 bg-gradient-to-r from-sky-700 to-sky-400 rounded-xl h-1/2"
  >
    <h1 class="my-20 text-3xl italic font-bold">
      {{ QuizStore.ResultMessage }}
    </h1>
    <p>Total Questions : {{ QuizStore.questions.length }}</p>
    <p>Correct Answers : {{ QuizStore.score }}</p>
  </div>
</template>
