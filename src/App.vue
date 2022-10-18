<script setup>
import {ref, onMounted, computed, watch} from 'vue'

const todos = ref([])
const name = ref('')

const inputContent = ref('')
const inputCategory = ref(null)

const todos_asc = computed(() =>{ todos.value.sort((a,b) =>{
  return b.createAt - a.createAt
})})

const addTodo = (()=>{})


watch(name,(newVal) =>{
  localStorage.setItem('name',newVal)
})

onMounted(() => {
  name.value = localStorage.getItem('name') || ''
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

    <section class="create-todo">
      <h3>Create A Todo</h3>

      <form @submit.prevent="addTodo">
        <h4>What's on your todo list?</h4>
        <input type="text" placeholder="e.g. cooking" v-model="inputContent"/>

        <h4>Pick a category</h4>

        <div class="options">
          <label>
            <input type="radio" name="caterogy" value="business" v-model="inputCategory"/>
            <span class="bubble business"></span>
            <div>Business</div>
          </label>

          <label>
            <input type="radio" name="caterogy" value="personal" v-model="inputCategory"/>
            <span class="bubble personal"></span>
            <div>Personal</div>
          </label>
        </div>
      </form>

    </section>
  </main>
</template>

<style scoped>

</style>
