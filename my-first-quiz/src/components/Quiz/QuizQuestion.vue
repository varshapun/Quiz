<script setup>
import { useQuizStore } from "../../stores/QuizStore";
import QuizOptions from "./QuizOptions.vue";
let QuizStore = useQuizStore();

defineProps({
  index: Number,
});
</script>
<template>
  <div class="p-10 text-2xl font-semibold bg-white rounded-xl h-1/2">
    <p class="my-2 text-red-500">{{ QuizStore.ErrorMessage }}</p>
    <h1 class="mb-5">
      ({{ QuizStore.questions[index].id }}) {{ QuizStore.questions[index].que }}
    </h1>
    <div>
      <QuizOptions
        v-for="(option, i) in QuizStore.questions[index].Options"
        :index="i"
        :option="option"
        class="pl-5"
        :key="i"
        @click="QuizStore.Result[index] = i + 1"
        :name="QuizStore.questions[index].id"
      />
    </div>
    <div class="my-20 text-right">
      <button
        @click.prevent="$emit('Next', index)"
        class="px-5 py-2 text-white bg-sky-500 rounded-xl"
      >
        Next
      </button>
    </div>
  </div>
</template>
