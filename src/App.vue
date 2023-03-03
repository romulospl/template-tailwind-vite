<script setup>
import { onMounted, ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'

const text = ref('')

onMounted(() => {
  axios.get('https://api.adviceslip.com/advice')
    .then(function (response) {
      text.value = response.data.slip.advice;
    })
})
</script>

<template>
  <header class="w-11/12 mx-auto">
    <nav class="w-full border border-slate-300 rounded-2xl py-2">
      <ul class="ml-10 w-fit mx-auto inline-flex">
        <li><img class="w-6 mr-2" src="./assets/vue.svg" /></li>
        <li class="mr-6">Routes: </li>
        <li>
          <router-link to="/">Home</router-link> |
        </li>
        <li class="ml-1">
          <router-link to="/about"> About</router-link>
        </li>
      </ul>
    </nav>
  </header>
  <main class="w-10/12 mx-auto">

    <div class="flex">

      <div>
        <div class="text-2xl text-slate-800">
          <code>Router View area:</code>
        </div>
        <div class="w-96 h-16 border text-slate-600 text-center">
          <router-view></router-view>
        </div>
      </div>

      <HelloWorld msg="Vite + Vue + pinia + router + tailwind + axios" />
    </div>


    <div class="mt-2">
      <span class="text-sm text-slate-400">Example axios, advice: </span>
      <span class="text-sm text-slate-400">{{ text }}</span>
    </div>
    
  </main>
  <footer class="mt-12 w-fit mx-auto">
    <span class="text-xs text-slate-400">By: romulospl</span>
  </footer>
</template>

<style scoped></style>
