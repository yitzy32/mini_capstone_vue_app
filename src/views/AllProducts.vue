<template>
  <div class="all-products">
    <h1>{{ message }}</h1>
    <!-- <p v-for="product in products">
      {{ product.name }}<br>
      {{ product.description }}
    </p> 
    <hr> -->
<div class="row">
  <div class="col-sm-4" v-for="product in products">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">{{ product.name }}</h5>
        <p class="card-text">{{ product.description }}</p>
        <a href="#" class="btn btn-primary">Show More</a>
      </div>
    </div>
  </div>
</div>    
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Index!",
      products: [],
    };
  },
  created: function () {
    console.log(this.productsIndex());
  },
  methods: {
    productsIndex: function () {
      console.log("in index");
      axios.get("/api/products").then((response) => {
        console.log(response.data);
        this.products = response.data;
      });
    },
  },
};
</script>