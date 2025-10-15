<template>
  <div id="app">
    <h2>Tareas completadas: {{ contadorCompletadas }} / {{ tasks.length }}</h2>
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>TASK</th>
          <th>STATUS</th>
          <th>ACTION</th>
        </tr>
      </thead>
      <tbody>
        <TaskItem
          v-for="task in tasks"
          :key="task.id"
          :task="task"
          @task-completed="manageStatus"
        />
      </tbody>
    </table>
  </div>
</template>

<script setup>
import TaskItem from './components/TaskItem.vue'
import { computed, ref } from 'vue'

const tasks = ref([
  { id: 1, name: "Estudiar Vue.js", done: false },
  { id: 2, name: "Practicar props", done: false },
  { id: 3, name: "Hacer el ejercicio", done: false },
]);

const manageStatus = (taskId) => {
  const taskToComplete = tasks.value.find(t => t.id == taskId);
  if (taskToComplete) {
    taskToComplete.done = true;
  }
};

const contadorCompletadas = computed(() => {
  return tasks.value.filter(t => t.done).length;
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
