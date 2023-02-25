<template>
  <div id="task">
    <form>
      <input 
        type="text" 
        placeholder="Tarefa de hoje"
      />
      <button type="submit">Adicionar</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Task-Component'
}
</script>

<style scoped>@import '../styles/task.css';</style>