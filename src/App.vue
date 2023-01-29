<template>
  <h1>To do list</h1>
  <label>Digite o título da tarefa: 
    <input type="text" v-model="todoItem.titulo" placeholder="Digite o título" />
  </label>
  <button @click="adicionarItem" >adicionar</button>

  <TodoItem v-for="item in todoList" :key="item.titulo" :item="item" @removerItem="removerItem" />
</template>

<script>
import TodoItem from "./components/TodoItem.vue"
export default {
  components: {
    // aqui vamos registrar o componente
    TodoItem
  },
  data(){
    return {
      todoItem: {
        titulo: "",
        finalizado: false
      },

      // aqui vamos armazenar as tarefas criadas
      todoList: []
    }
  },
  methods: {
    adicionarItem(){
      if(!(!!this.todoItem.titulo)){
        alert("O título não pode ficar vazio!")
        return
      }

      if(!!this.todoList && this.todoList.filter(item => item.titulo == this.todoItem.titulo).length > 0){
        alert("Já existe uma tarefa com este título!")
        this.todoItem.titulo = ""
        return
      }

      // spread operator ...
      // this.todoList.push({titulo: this.todoItem.titulo, finalizado: this.todoItem.finalizado})
      this.todoList.push({...this.todoItem})

      this.todoItem.titulo = ""
    },
    removerItem(item){
      this.todoList = this.todoList.filter(x => x.titulo != item.titulo)
    }
  },
}
</script>

<style>

</style>