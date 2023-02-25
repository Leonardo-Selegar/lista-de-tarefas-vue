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
    <span v-show="tarefas.length > 0">
      Você tem <strong :class="{pend: pendente}">{{ tarefas.length }}</strong> tarefas pendentes
    </span>
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
      pendente: false
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
  watch:{
    tarefas:{
      deep: true,
      handler(){
        localStorage.setItem('tasks', JSON.stringify(this.tarefas));
        this.tarefas.length > 4 ? this.pendente = true : this.pendente = false;
      }
    }
  },
  created(){ //chamado apos a instancia do vue ser criada
    const json = localStorage.getItem('tasks');
    this.tarefas = JSON.parse(json) || [];
  }
}
</script>

<style scoped>@import '../styles/task.css';</style>
