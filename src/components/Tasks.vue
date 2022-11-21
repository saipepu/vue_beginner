<template>
  <div :key="task.id" v-for="task in tasks" class="tasks">
    <Task @toggle-reminder="$emit('toggle-reminder', task.id)" :task="task" @onDelete="$emit('onDelete', task.id)"/>
  </div>
</template>

<script>
import Task from './Task'

export default {
  name: 'Tasks',
  props: {
    tasks: Array
  },
  components: {
    Task
  },
  emits: ['toggle-reminder', 'onDelete']
}
</script>
<style scoped>
.tasks {
  width: 100%;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>