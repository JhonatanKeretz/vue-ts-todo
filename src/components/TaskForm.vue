
<template>
<div class="col-md-4 offset-md-4">
   <form @submit.prevent="saveTask()" class="card card-body">

   <h1 class="text-center h3 mb-3">Criar Ações</h1>
  <input type="text" placeholder="Qual a ação" v-model="task.title" autofocus
   class="form-control mb-3">

  <textarea rows="3" placeholder="Qual a descrição da Ação" v-model="task.description"
  class="form-control mb-3"></textarea>

  <button class="btn btn-primary"
  :disabled="!task.title || !task.description"
  >Salvar</button>
 </form>
</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { Task } from '@/interfaces/Task'
import { createTask } from '@/services/TaskService'

export default defineComponent({
  data(){
    return {
      task: {

      } as Task,
    };
  },
  methods:{
   async saveTask(){
      const res = await createTask(this.task);
      console.log(res);
      this.$router.push({ name: "task" });
    }
  }
});

</script>

<style>

</style>