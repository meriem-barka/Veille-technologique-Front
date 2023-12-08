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

<style scoped>
.kanban-board {
  display: flex;
  flex-wrap: nowrap;
  justify-content: flex-start;
  align-items: flex-start;
}

.lane {
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f4f4f4;
}

.lane-title {
  font-size: 18px;
  font-weight: bold;
}

.column {
  margin: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background-color: #fff;
  width: 250px;
}

.tasks {
  margin-top: 10px;
}

.task {
  margin: 5px 0;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 3px;
  background-color: #fcfcfc;
}

.task h3 {
  margin: 0;
  font-size: 16px;
}

.task p {
  margin: 5px 0 0 0;
  font-size: 14px;
}

button {
  margin-top: 10px;
  padding: 8px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  background-color: #4caf50;
  color: #fff;
  font-size: 14px;
}

button:hover {
  background-color: #45a049;
}
</style>
