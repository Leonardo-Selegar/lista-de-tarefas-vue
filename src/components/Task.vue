<template>
  <div id="task">
    <form @submit="addTask">
      <input 
        type="text" 
        placeholder="Tarefa de hoje"
        v-model="tarefa"
      />
      <button type="submit">Adicionar</button>
    </form>
    <Item :lista="tarefas" @remove="tarefas = $event"/>
  </div>
</template>

<script>
import Item from './Item';
export default {
  name: 'Task-Component',
  components:{
    Item,
  },
  data(){
    return{
      tarefa: '',
      tarefas: [],
      key: 0,
      removeKey: 0,
    }
  },
  methods:{
    addTask(e){
      e.preventDefault();
      if(this.tarefa.length !== 0){
        this.tarefas.push({
          text: this.tarefa,
          key: this.key,
        });
        this.key++
      } else {
        alert('Digite uma tarefa...');
        return;
      }
      this.tarefa = '';
    }
  },
}
</script>

<style scoped>@import '../styles/task.css';</style>