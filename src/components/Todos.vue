<template>
  <div>
    <div class="container">
      <h1>Bouh!</h1>
      <h2>C'est casper</h2>
      <h3>Le petit fantôme</h3>
      <form class="form-group">
        <label for="list"> </label>
        <input type="text" class="form-control" v-model="element" placeholder="Type a ghost quality" />
        <button class="btn" v-on:click.prevent="submitHandler">Add spooky</button>
      </form>
      <p>{{ element }}</p>
      <ul>
        <li v-for="element in listElement" :key="element">{{ element }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todos",
  data() {
    return {
      listElement: ["White", "Scary", "Nice"],
      element: "",
    };
  },
  methods: {
    submitHandler() {
      this.listElement.push(this.element);
    },
  },
};
</script>
