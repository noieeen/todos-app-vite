<script setup>
import {ref,onMounted, computed, watch} from 'vue'

const todos = ref([])
const name = ref('')

const inputContent = ref('')
const inputCategory = ref(null)

const todos_asc = computed(() =>{ todos.value.sort((a,b) =>{
  return b.createAt - a.createAt
})})

watch(name,(newVal) =>{
  localStorage.setItem('name',newVal)
})

</script>

<template>
  <main class="app">
    <section class="greeting">
      <h2 class="title">
        What's up, <input type="text" placeholder="Name here"
        v-model="name" />
      </h2>
    </section>
  </main>
</template>

<style scoped>

</style>
