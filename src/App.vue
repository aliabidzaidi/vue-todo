<template>
  <div class="container">
    <Header title="Task Tracker" />

    <Tasks @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      // console.log("task received ", id);
      if(confirm('Are you sure you want to delete this Task?'))
        this.tasks = this.tasks.filter((task) => task.id !== id);
    },
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
  margin-top: 10px;
  /* border: 3px solid salmon; */
}

.btn-group {
  margin: 10px;
}
</style>
