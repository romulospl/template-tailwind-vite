<script setup>
import { mapActions, storeToRefs } from 'pinia';
import { ref } from 'vue'
import { useMainStore } from '../store/main';

defineProps({
  msg: String,
})

const mainStore = useMainStore()

const count = ref(0)

const { counter } = storeToRefs(mainStore)
const { increment } = mapActions(useMainStore, ["increment"])
</script>

<template>
  <div class="w-full mx-auto">

    <div class="text-center">
      <span>{{ msg }}</span>
    </div>

    <div class="w-fit mx-auto mt-8">
      <div>
        <span>Pinia example: </span>
      </div>
      <button class="border border-slate-300 px-6 py-2 rounded-3xl" type="button" @click="increment">count is {{ counter }}</button>
    </div>
    
  </div>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
