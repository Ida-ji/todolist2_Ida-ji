<!-- src/components/ItemList.vue -->
<script setup lang="ts">
import { ref } from 'vue'

interface Task {
  name: string
  isdone: boolean
}

const tasks = ref<Task[]>([
  { name: '文化人類学', isdone: false},
  { name: 'デーサイ', isdone: false}
])

const newTaskName = ref('') 
const newTaskisdone = ref(false) 

const addTask = () => { 
  if (newTaskName.value.trim() === '') return
  if (tasks.value.some((task) => task.name === newTaskName.value)) return
  tasks.value.push({ name: newTaskName.value, isdone: newTaskisdone.value }) 
  newTaskName.value = ''
} 
const DoneTask = (name: string) => { 
  const task = tasks.value.find((task) => task.name === name)
  if (task) {
    task.isdone = true
  }
} 

const deleteTask = (name: string) => { 
  tasks.value = tasks.value.filter((task) => task.name !== name) 
} 
</script>

<template>

  <div>
    <div>DoneList</div>
    <ul>
      <li v-for="task in tasks" :key="task.name">
        <div v-if="task.isdone === true">
          <div>名前: {{ task.name }}</div>
          <div>状態: {{ task.isdone }} </div>
          <button @click="deleteTask(task.name)">削除する</button>
        </div>
      </li>
    </ul>
      <div>NotDoneList</div>
    <ul>
      <li v-for="task in tasks" :key="task.name">
        <div v-if="task.isdone === false">
          <div>名前: {{ task.name }}</div>
          <div>状態: {{ task.isdone }} </div>
          <button @click="DoneTask(task.name)">完了する</button>
        </div>
      </li>
    </ul>
        <div>
      <label>
        名前
        <input v-model="newTaskName" type="text" />
      </label>
      <button @click="addTask">追加</button>
    </div>
  </div>
</template>

<style></style>