<template>
  <main>
    <h1>Quadro de Tarefas</h1>
    <p>Criar uma lista de tarefa</p>

    <div class="create-new">
      <input type="text" v-model="newTask" placeholder="Adicionar Tarefa" @keypress.enter="addTask" >
      <button @click="addTask" >Adicionar</button>
    </div>

    <div class="tasks">
      <Task v-for="(task, i) in $store.state.tasks" 
      :key="i" :task="task" />
    </div>
  </main>
</template>

<script>
import Task from '../components/Task.vue'
export default {
  data(){
    return{
      newTask: ''
    }
  },
  methods:{
    addTask(){
      if(this.newTask){
        this.$store.commit('ADD_TASK', this.newTask)
        this.newTask = ''
      }
    }
  },
  name: 'IndexPage'
}
</script>
