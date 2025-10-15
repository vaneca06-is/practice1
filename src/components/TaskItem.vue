<template>
  <tr>
    <td>{{ task.id }}</td>
    <td :style="{ textDecoration: task.done ? 'line-through' : 'none' }">
      {{ task.name }}
    </td>
    <td>{{ task.done }}</td>
    <td>
      <span v-if="task.done">✅</span>
      <button
        v-if="!task.done"
        @click="emitCompletion"
      >
        Completar
      </button>
    </td>
  </tr>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  task: {
    type: Object,
    required: false,
  },
});

const emit = defineEmits(['task-completed']);

const emitCompletion = () => {
  emit('task-completed', props.task.id);
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}
</style>