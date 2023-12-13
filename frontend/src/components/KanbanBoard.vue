<template>
  <h1 class="lane-title">Bienvenue</h1>
  <div class="kanban-board">
    <column
      v-for="column in columns"
      :key="column.id"
      :column-name="column.name"
      :tasks="column.tasks"
      @deleteTask="deleteTask"
    />
    <button @click="addColumn">Ajouter une colonne</button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Column from "./Column.vue";

const columns = ref([]);

function addColumn() {
  const newColumn = {
    id: columns.value.length + 1,
    name: "Nouvelle colonne",
    tasks: [],
  };
  columns.value.push(newColumn);
}

function deleteTask(taskId) {
  columns.value.forEach((column) => {
    column.tasks = column.tasks.filter((task) => task.id !== taskId);
  });
}
</script>

<style scoped></style>
