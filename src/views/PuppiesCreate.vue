<template>
  <div class="PuppiesCreate">
    <h1>{{ message }}</h1>
    <div> 
      Name: <input type="text" v-model="newPuppyParams.name" />
      Age: <input type="text" v-model="newPuppyParams.age" />
      Breed: <input type="text" v-model="newPuppyParams.breed" />
      <p>
        <button v-on:click="puppyCreate">Add New</button>
      </p>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Create New Puppy!",
      newPuppyParams: {},
      puppies: [],
    };
  },
  created: function () {
    // this.puppyCreate();
  },
  methods: {
    puppyCreate: function () {
      console.log("creating new puppy...");
      axios.post("/puppies", this.newPuppyParams).then((response) => {
        console.log(response.data);
        this.puppies.push(response.data);
        this.newPuppyParams = {};
      });
    },
  },
};
</script>