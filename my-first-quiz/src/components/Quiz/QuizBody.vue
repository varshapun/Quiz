<script setup>
import QuizQuestion from "./QuizQuestion.vue";
import { useQuizStore } from "../../stores/QuizStore";
import { ref } from "vue";
import QuizResult from "./QuizResult.vue";
let QuizStore = useQuizStore();
let index = ref(0);
function validate(i) {
  if (!QuizStore.Result[i]) {
    QuizStore.ErrorMessage = "please select any option!";
  } else {
    QuizStore.ErrorMessage = "";
    if (i <= 4) {
      index.value += 1;
    }
    if (i === 4) {
      QuizStore.generateResult();
    }
  }
}
</script>
<template>
  <div class="grid items-center w-10/12 mx-auto" style="height: 90vh">
    <QuizQuestion
      v-if="index <= 4"
      :index="index"
      class="w-10/12 mx-auto"
      @Next="validate"
    />
    <QuizResult v-show="index > 4" />
  </div>
</template>
