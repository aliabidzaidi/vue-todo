<template>
  <div :class="[task.reminder ? 'reminder' : '','task']">
    <h3>
      {{ task.text }}
      <i @click="deleteTodo(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>


<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    deleteTodo(id){
      // console.log(`Delete this bad boy ${id}!!`)
      this.$emit('delete-task', id);
    }
  },
};
</script>



<style scoped>
  .task{
    margin: 15px;
    background: #f4f4f4;
    padding: 10px 20px;
    cursor: pointer;
    text-align: left;
  }

  .task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .task.reminder{
    border-left: 5px solid green;
  }

  .fas{
    color: red;
  }
</style>