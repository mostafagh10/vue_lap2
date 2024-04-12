<template>
    <div class="d-flex align-items-baseline justify-content-between bg-dark text-light p-2 m-2">
      <a href="#" style="color: yellow; text-decoration: none;" @click.prevent="showBooks">Books</a>
      <div class="align-items-baseline d-flex">
        <button class="btn btn-primary" @click="showWishlist">Wishlist</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    methods: {
      showBooks() {
        this.$emit('show-books');
      },
      showWishlist() {
        this.$emit('show-wishlist');
      }
    }
  };
  </script>
  
  <style>

  </style>
  