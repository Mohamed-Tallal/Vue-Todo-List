<template>
  <div class="card mb-1 text-left">
      <div v-if="tasks.length == 0" class="d-flex justify-content-center">
         <h4> Currently there are no Tasks </h4>
      </div>
      <div v-else> 
          <ul class="list-group " v-for="(task,index) in tasks" :key="index">
          <li class="list-group-item ">
              <div :class="task.complete == true ? 'complete' : ''">{{task.name}}</div>
          <div class="icons iconHover">
              <i class="far fa-check-circle mr-1 "  @click=" complete(task)"></i>
              <i class="fas fa-trash-alt mr-1 ml-2" @click="deleteTask(index)"></i>
          </div>
          </li>
      </ul>
      </div>
  </div>
</template>
<script>
export default {
    props:{
    tasks:null,
    },
    methods:{
        complete(task){
            this.$emit('completeEvent', task)
        },
        deleteTask(index){
            this.$emit('deleteEvent',index)
        }
    }
    
}
</script>
<style scoped>
.card{
  padding: 30px;
 background: #eee;

}
.complete{
    color: #28a745;
    text-decoration:line-through ;
}
.list-group-item{
   display: flex;
   justify-content: space-between;
}
.iconHover{
    cursor: pointer;
}
</style>

