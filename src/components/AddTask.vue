<template>
  <form action="" class="add-form" @submit="OnSubmit">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        name="day"
        v-model="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input v-model="reminder" type="checkbox" name="reminder"/>
    </div>
    <button @click="text ? $emit('toggle-form') : ''" type="submit">Create Task</button>
  </form>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    OnSubmit(e) {
      e.preventDefault();
      if(!this.text) {
        alert('Please add a task')
        return
      }
      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }
      this.$emit('add-task', newTask)
      console.log(newTask)
      this.text = ''
      this.day = ''
      this.reminder = false
    }
  }
}
</script>
<style scoped>
.add-form {
  width: fit-content;
  min-width: 250px;
  display: flex;
  flex-direction: column;
  align-items: start;
  justify-content: start;
}
.form-control {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: start;
  margin-bottom: 10px;
}
input {
  width: 100%;
  padding: 5px;
  border: 1px solid #7d7d7d;
  border-radius: 3px;
}
input:focus {
  outline: none;
}
.form-control-check {
  flex-direction: row-reverse;
  gap: 10px;
}
.form-control-check > input {
  width: fit-content;
}
button {
  width: 100%;
  color: white;
  background: green;
  border: none;
  border-radius: 5px;
  padding: 5px 0px;
}
</style>