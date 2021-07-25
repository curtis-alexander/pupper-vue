<template>
  <div class="Puppies">
    <h1>{{ message }}</h1>
    <div v-for="puppy in puppies" v-bind:key="puppy.id">
    <p>ID: {{ puppy.id }}</p>
    <p>Name: {{ puppy.name }}</p>
    <p>Age: {{ puppy.age }}</p>
    <p>Breed: {{ puppy.breed }}</p>
    <hr />
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to the Index Page!",
      puppies: [],
    };
  },
  created: function () {
    this.getPuppies();
  },
  methods: {
    getPuppies: function () {
      console.log("getting puppies...");
      axios.get("/puppies").then((response) => {
        console.log(response.data);
        this.puppies = response.data;
      });
    },
  },
};
</script>
