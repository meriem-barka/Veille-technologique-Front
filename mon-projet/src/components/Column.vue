<template>
  <div class="column">
    <h2>{{ columnName }}</h2>
    <div class="tasks">
      <task
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @deleteTask="deleteTask"
      />
    </div>
    <button @click="addTask">Ajouter une tâche</button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Task from "./Task.vue";

const columnName = ref("");
const tasks = ref([]);

function addTask() {
  const newTask = {
    id: tasks.value.length + 1,
    name: "Nouvelle tâche",
    description: "",
  };
  tasks.value.push(newTask);
}

function deleteTask(taskId) {
  tasks.value = tasks.value.filter((task) => task.id !== taskId);
}
</script>

<style scoped>
/* Styling for the column component */
</style>
