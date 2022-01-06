<template>
  <div class="container mt-5">
  <div class="row">
  <div class="form-inLine">
    <b-form-input v-model="newTask" placeholder="Add new task" @keyup.enter="add"></b-form-input> 
    <b-button class ="ml-2" variant="primary" @click="addTask">Add</b-button>
  </div>
  </div>
   
<div class="row mt-3">
  
  <div class="col-md-3">
    <div class="p-2 alert alert-secondary">
      <h3>Backlog </h3>
      <draggable class="list-group" :list="taskBackLog" group = "tasks">
        <div class="list-group-item" v-for="element in taskBackLog" :key="element.name">{{element.name}}</div>
      </draggable>
    </div>
  </div>

  <div class="col-md-3">
    <div class="p-2 alert alert-primary">
      <h3>In Progress </h3>
      <draggable class="list-group" :list="taskInProgress" group = "tasks">
        <div class="list-group-item" v-for="element in taskInProgress" :key="element.name">{{element.name}}</div>
      </draggable>
    </div>
  </div>

  <div class="col-md-3">
    <div class="p-2 alert alert-warning">
      <h3>Done </h3>
      <draggable class="list-group" :list="taskDone" group = "tasks">
        <div class="list-group-item" v-for="element in taskDone" :key="element.name">{{element.name}}</div>
      </draggable>
    </div>
  </div>
</div>

  </div>
</template>

<script>
import draggable from "vuedraggable";
export default {
  name: "kanban-board",
  components: {
    draggable
  },
  data(){
    return{
      newTask: "",
      taskBackLog:[
        {name:"Task A"},
        {name:"Task B"},   
        {name:"Task C"},  
      ],
      taskInProgress:[
      ],
      taskDone:[]
    }
  },
  methods:{
    addTask(){
      if(this.newTask){
        this.taskBackLog.push({name: this.newTask});
        this.newTask = "";//Blank string to clear out the text box
      }
    }
  }
}
</script>

<style>

</style>
