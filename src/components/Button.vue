<template>
  <button @click="onClick()" class="btn" :style="{backgroundColor: color, color: textColor}">Add Task</button>
</template>


<script>
export default {
  name: 'Button',
  props: {
    color: String,
    textColor: String,
    content: String
  },
  methods: {
    onClick() {
      console.log('click')
    }
  }
}

</script>