<template>
  <div id="app">
    <header>Minhas Tarefas</header>
    <Task />
  </div>
</template>

<script>
import Task from './components/Task.vue';
export default {
  name: 'App',
  components:{
    Task
  }
}
</script>

<style scoped>@import './styles/app.css';</style>
