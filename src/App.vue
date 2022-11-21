<template>
  <HeaderVue title="Todo App Vue Js" @toggle-form="ToggleForm"/>
  <router-view :toggleForm="showForm">

  </router-view>
  <Footer />
</template>

<script>

import HeaderVue from './components/HeaderVue';
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    HeaderVue,
    Footer
  },
  data() {
    return {
      showForm: false
    }
  },
  methods: {
    ToggleForm() {
      console.log(this.showForm)
      this.showForm = !this.showForm
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
