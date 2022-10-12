<script setup>
import { useQuizStore } from "../../stores/QuizStore";
let QuizStore = useQuizStore();
let props = defineProps({
  option: String,
  index: Number,
  name: Number,
});
</script>
<template>
  <div>
    <input
      type="radio"
      :id="name + index"
      v-model="QuizStore.questions[name - 1].checked[index]"
      :name="name"
      class="mr-5"
      :value="option"
    />
    <label :for="name + index" class="mr-5">{{ option }}</label>
  </div>
</template>
