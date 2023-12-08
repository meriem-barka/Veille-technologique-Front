<template>
  <div class="task">
    <h3>{{ task.name }}</h3>
    <p>{{ task.description }}</p>
    <button @click="editTask">Modifier</button>
    <button @click="deleteTask">Supprimer</button>
  </div>
</template>

<script setup>
import { ref, defineProps, getCurrentInstance } from "vue";

const props = defineProps(["task"]);
const { emit } = getCurrentInstance();

function editTask() {
  const newName = prompt("Nouveau nom de la tâche", props.task.name);
  if (newName !== null) {
    props.task.name = newName;
  }

  const newDescription = prompt(
    "Nouvelle description de la tâche",
    props.task.description
  );
  if (newDescription !== null) {
    props.task.description = newDescription;
  }
}

function deleteTask() {
  emit("deleteTask", props.task.id);
}
</script>

<style scoped>
.task {
  margin: 10px;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: box-shadow 0.3s ease-in-out;
}

.task:hover {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.task h3 {
  margin: 0 0 10px 0;
  font-size: 18px;
  font-weight: bold;
}

.task p {
  margin: 0 0 15px 0;
  font-size: 16px;
}

button {
  margin-top: 10px;
  padding: 8px 12px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  background-color: #e44d26;
  color: #fff;
  font-size: 14px;
  transition: background-color 0.3s ease-in-out;
}

button:hover {
  background-color: #d6361d;
}
</style>
