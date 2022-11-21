<template>
  {{toggleForm}}
  <Form @add-task="AddTask" @toggle-form="ToggleForm" v-show="showForm"/>
  <TasksVue :tasks="tasks" @onDelete="DeleteTask" @toggle-reminder='ToggleReminder'/>
</template>

<script>
import TasksVue from '../components/Tasks.vue';
import Form from '../components/AddTask.vue';

export default {
  name: 'Home',
  components: {
    Form,
    TasksVue
  },
  props: {
    toggleForm: Boolean,
  },
  data() {
    console.log('Home', this.toggleForm)
    return {
      tasks: [],
      showForm: this.toggleForm ? this.toggleForm : false
    }
  },
  methods: {
    ToggleForm() {
      console.log('submitted should be closed')
      this.showForm = !this.showForm
    },
    DeleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    ToggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id == id ? Object.assign(task, {reminder: !task.reminder}) : task)
    },
    AddTask(task) {
      this.tasks.push(task)
      console.log(this.tasks)
    },
    async fetchTasks() {
      const res = await fetch('http://localhost:3001/tasks')
      const data = await res.json()
      console.log(data)
      return data
    }
  },
  async created() {
    this.tasks = await this.fetchTasks();
    console.log('reloaded')
    this.$watch('toggleForm', () => {
      this.showForm = this.toggleForm
    })
  }
}
</script>