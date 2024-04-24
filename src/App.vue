<template>
  <div class="container">
    <AppHeader :toggleForm="toggleForm" @show-add-form="showAddbutton" title="Task Tracker " />
    <div v-if="toggleForm">
     <AddTask  @add-new-task="addNewTask" />
    </div>
    <AppTasks @delete-task="deleteTask" @toggle-reminder="toggleReminder" :tasks="tasks" />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppTasks from './components/AppTasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppTasks,
    AddTask
  },
  data(){
    return {
      tasks: [],
      toggleForm: false
    }
  },
  emits: ['add-new-task'],
  methods: {
    showAddbutton(){
      this.toggleForm = !this.toggleForm;
    },
    addNewTask(newTask){
      this.tasks.push(newTask)
  },
    deleteTask(id){
      if(confirm('Are you sure')){
      this.tasks = this.tasks.filter((task) => task.id != id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) =>  
        task.id === id ? {...task, reminder: !task.reminder } :task
      )
    },
    
  },
  
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Apointment",
        day: "March 1st at 2: 30pm",
        reminder: true
      },
      {
        id: 2,
        text: "Meeting at school",
        day: "March 3rd at 3: 30pm",
        reminder: true
      },
      {
        id: 3,
        text: "Food Shooping",
        day: "June 1st at 6: 30pm",
        reminder: false
      },
    ]
  },
}
</script>


<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>