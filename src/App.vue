<template>
<div class="container">
  <Header @showForm="showForm" title="Task Tracker" :toggleText="showAddTask" />
  <div v-show="showAddTask">
  <AddTask @addDataTask="addTask"/>
  </div>
  <Tasks @toggle-reminder="toggleTask" @delete-task="deleteTask" :tasks="tasks" />
</div>
  
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return{
    tasks: [],
    showAddTask: false
    }
  },
  methods: {
    deleteTask(id){
      confirm("are you sure") ? this.tasks = this.tasks.filter((tass) => tass.id !== id) : null  
    },
    toggleTask(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    },

    addTask(newTask){
      this.tasks = [...this.tasks, newTask]
    },

    showForm(){
      this.showAddTask = !this.showAddTask
    }
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctor app',
        date: new Date(),
        reminder: true,
      },
      {
        id: 2,
        text: 'Work',
        date: new Date(),
        reminder: true,
      },
      {
        id: 3,
        text: 'Interview',
        date: new Date(),
        reminder: false,
      },
    ]
  },
};
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
