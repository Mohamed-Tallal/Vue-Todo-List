<template>
<h1 class="text-center mt-5 mb-5 ">{{tittle}}</h1>
<div :class="errorClass"  id="alert" role="alert">
  {{msg}}
</div>
<div class="d-flex m-3">
  <input type="text" class="form-control w-100" v-model="taskTittle">
  <button class="btn btn-outline-success ml-2 pl-3 pr-3 " @click="addTask" > Add </button>
</div>
<Todo :tasks="tasks"  v-on:completeEvent="completeTask"  v-on:deleteEvent="deleteTask"/>
</template>

<script>
import Todo from './components/TodoApp.vue'

export default {
  name: 'App',
  components: {
   Todo
  },
  data(){
    return{
      tittle : 'Todo List App',
      taskTittle:'',
      msg:null,
      errorClass :'alert alert-danger alert-style',
      tasks:[
        {
          name: 'Learn Vue Js',
          complete: false
        },
        {
          name: 'Learn Doker',
          complete: false
        },
        {
          name: 'Learn Nuxt Js',
          complete: false
        },
        {
          name: 'Learn Algoritms',
          complete: false
        }
      ],
    
      }
    },
    methods:{
        addTask(){
          if (this.taskTittle != '' ){
          this.errorClass = 'alert alert-success alert-error'
          this.tasks.unshift({
          name: this.taskTittle,
          complete: false
        });
          this.msg="The task has been added successfully";
          this.taskTittle = ''
          }else{
           this.msg="Enter Your Task";
            this.errorClass = "alert alert-danger alert-error"
          }
        },

        completeTask(task){
        if(task.complete == false){
          task.complete = true
        }else{
          task.complete = false

        }
        console.log(task.complete)
        },
        deleteTask(index){
          this.tasks.splice(index,1)
          this.errorClass = 'alert alert-success alert-error'
          this.msg="The task has been deleted successfully";
        }
         
    }
}
</script>

<style>

.alert-style{
display: none;
}
.alert-error{
  display: block;
}
</style>
