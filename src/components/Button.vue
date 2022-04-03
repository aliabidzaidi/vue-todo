<template>
  <button @click="onClick()" :style="{ background: color }" class="btn">
    {{ text }}
  </button>
</template>


<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
      // console.log("Button Clicked");
      this.$emit('toggle-add-task')
    },
  },
};
</script>


<style scoped>
.btn {
  margin: 10px;
  padding: 10px;
  font-size: 14px;
  font-weight: 500;
  color: white;
  border: none;
  border-radius: 5px;
}
</style>


