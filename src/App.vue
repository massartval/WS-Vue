<template>
  <div>
    <headerList></headerList>
  </div>
</template>

<script>
import HeaderList from './components/HeaderList.vue'

export default {
  name: 'App',
  components: {
    'headerList' : HeaderList
  }
}
</script>

<style>
body {
  background-color: #9cdcc4;
}
button {
  background-color: #41b783 !important;
}
</style>
