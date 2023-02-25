<template>
  <div id="item">
    <ul>
      <li v-for="task in lista" :key="task.key">
        <span>{{task.text}}</span>
        <button @click="deleteItem(task.key)">Concluir</button>
      </li>

    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Item-component',
    props:[
      'lista',
    ],
    data(){
      return{
        newList: [],
      }
    },
    methods:{
      deleteItem(key){
        this.newList = this.lista.filter((item) => item.key !== key);
        this.$emit('remove', this.newList);
        }
      }
    }
</script>

<style scoped>@import '../styles/item.css';</style>