<script setup>
import CustomButton from '../components/CustomButton.vue'
import { store } from '@/store/index'
import { useRouter } from 'vue-router'

const questions = store.questions
const router = useRouter()
</script>

<template>
  <main class="text-center w-full flex-col gap-5 flex p-5">
    <h5 class="text-xl">List Soal</h5>
    <div class="flex gap-2 flex-wrap">
      <span
        v-for="(question, idx) in questions"
        :key="idx"
        @click="router.push({ name: 'question', hash: '#question-' + question.id })"
        :class="[
          'cursor-pointer w-10 h-10 flex items-center justify-center rounded',
          question.selectedAnswer.length
            ? 'bg-green-600 hover:bg-green-700 text-white'
            : 'bg-sky-200 hover:bg-sky-300'
        ]"
        >{{ idx + 1 }}</span
      >
    </div>
    <div>
      <CustomButton text="KEMBALI" type="secondary" @click="router.back()" />
    </div>
  </main>
</template>
