<template>
  <header>
    <h1>{{ title }}</h1>
    <Button 
    @click="$emit('toggle-form')"
    color="green" textColor="white" content="add tasks"   />
  </header>
</template>

<script>
import Button from './Button'

export default {
  name: 'Header',
  props: {
    title: {
      type: String,
      default: 'Hello world',
    }
  },
  components: {
    Button
  }
}
</script>

<style scoped>

</style>