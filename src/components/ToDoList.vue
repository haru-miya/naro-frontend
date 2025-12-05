<script setup lang="ts">
import { ref } from 'vue'

interface ToDo {
    task: string
    done: boolean
}

const toDos = ref<ToDo[]>([
    { task: '買い物', done: false },
    { task: '掃除', done: true },
    { task: '運動', done: false }
])
const newTask = ref('')

const addToDo = () => {
    toDos.value.push({ task: newTask.value, done: false })
    newTask.value = ''
}

const toggleDone = (toDo: ToDo) => {
    toDo.done = !toDo.done
}
</script>

<template>
    <div>
        <div>ToDoList</div>
        <ul>
            <li v-for="toDo in toDos" :key="toDo.task">
                <label>
                    <input type="checkbox" v-model="toDo.done" @click="toggleDone(toDo)" />
                    <span :style="{ textDecoration: toDo.done ? 'line-through' : 'none' }">{{ toDo.task }}</span>
                </label>
            </li>
        </ul>
        <div>
            <label>
                新しいタスク
                <input v-model="newTask" type="text" />
            </label>
            <button @click="addToDo">追加</button>
        </div>
    </div>
</template>

<style></style>