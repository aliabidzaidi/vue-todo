<template>
  <div class="container">
    <Header title="Task Tracker" @toggle-add-task="toggleAddTask" :showAddTask="showAddTask"/>
    <div v-if="showAddTask"> <!-- v-show -->
      <AddTask @add-task="addTask"/>
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header"
import Tasks from "./components/Tasks"
import AddTask from "./components/AddTask"

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    addTask(newTask){
      this.tasks = [...this.tasks, newTask]
    },

    deleteTask(id) {
      // console.log("task received ", id);
      if(confirm('Are you sure you want to delete this Task?'))
        this.tasks = this.tasks.filter((task) => task.id !== id);
    },

    toggleReminder(id){
      // console.log('Status change kro mera :', id)
      this.tasks = this.tasks.map((task)=> task.id === id ? { ...task, reminder: !task.reminder}: task)
    },

    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Learn Vue JS",
        day: "28/1/2022",
        reminder: true,
      },
      {
        id: 2,
        text: "Explore Vuetify",
        day: "5/2/2022",
        reminder: false,
      },
      {
        id: 3,
        text: "Kick start quasar",
        day: "10/2/2022",
        reminder: false,
      },
      {
        id: 4,
        text: "Dive into VPP",
        day: "30/1/2022",
        reminder: true,
      },
    ];
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 10px; */
  width: 50%;
  margin: auto;
  padding: 20px;
  background-color: #ebebeb;
  /* border: 3px solid salmon; */
}

.btn-group {
  margin: 10px;
}
</style>
