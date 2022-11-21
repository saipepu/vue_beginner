<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{task.text}}
      <i @click="DeleteTask(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{task.day}}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object
  },
  methods: {
    DeleteTask(id) {
      this.$emit('onDelete', id)
    }
  },
  emits: ['toggle-reminder']
}
</script>
<style scoped>
.task {
  width: fit-content;
  min-width: 250px;
  padding: 5px 10px;
  background: #EEEEEE;
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: start;
}
.reminder {
  border-left: 5px solid green;
}
.task > * {
  margin: 0;
}
h3 {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
</style>