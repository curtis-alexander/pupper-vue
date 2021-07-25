<template>
  <div class="Puppies">
    <h1>{{ message }}</h1>
    <div>
    <p>ID: {{ puppy.id }}</p>
    <p>Name: {{ puppy.name }}</p>
    <p>Age: {{ puppy.age }}</p>
    <p>Breed: {{ puppy.breed }}</p>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Show a Puppy!",
      puppy: {},
    };
  },
  created: function () {
    this.getPuppy();
  },
  methods: {
    getPuppy: function () {
      console.log("getting a puppy...");
      axios.get(`/puppies/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.puppy = response.data;
      });
    },
  },
};
</script>
