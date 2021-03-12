<template>
  <div>
    <headerList></headerList>
    <todos></todos>
  </div>
</template>

<script>
import HeaderList from "./components/HeaderList.vue";
import Todos from "./components/Todos.vue";

export default {
  name: "App",
  components: {
    headerList: HeaderList,
    todos: Todos,
  },
};
</script>

<style>
body {
  background-color: #9cdcc4;
}
button {
  background-color: #41b783 !important;
  color: white;
  font-weight: 800;
}
</style>
