<template>
  <header>
    <h1>{{ title }}</h1>
    <div class="btn-group">
    <Button 
    :color="showAddTask ? 'red': 'green'" 
    :text="showAddTask ? 'Close' : 'Add Task'" 
    @toggle-add-task="$emit('toggle-add-task')"/>
    <!-- <Button v-on:click="onClick()" color="green" text="Add Task"/> -->
    <!-- <Button color="blue" text="Update Task"/>
    <Button color="red" text="Delete Task"/> -->
    </div>
  </header>
</template>

<script>
import Button from './Button.vue'

export default {
  name: "Header",
  props: {
      title: String,
      showAddTask: Boolean,
  },
  components: {
    Button
  }
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 5px;
  /* margin-bottom: 20px; */
}
</style>