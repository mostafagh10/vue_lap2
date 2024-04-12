<template>
    <div class="row bg-dark p-2 m-2">
      <div v-for="book in books" :key="book.id" class="card mx-auto my-2 text-center" style="width: 26rem; margin: 0.2rem;">
        <img :src="book.imageLink" height="300" />
        <h4 class="my-1">{{ book.title }}</h4>
        <p>Author: {{ book.author }}</p>
        <p :class="[book.pages >= 200 ? 'more' : 'less']">Pages: {{ book.pages }}</p>
        <button class="btn btn-primary" @click="addToWishlist(book)" :disabled="isInWishlist(book)">Add to Wishlist</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['books', 'wishlist'],
    methods: {
      addToWishlist(book) {
        this.$emit('add-to-wishlist', book);
      },
      isInWishlist(book) {
        return this.wishlist && this.wishlist.some(item => item.book.title === book.title);
      }
    }
  };
  </script>
  
  <style>
    .more,.less{
        font-weight: bold;
    }
    .more{
        color: green;
    }
    .less{
        color: red;
    }
  </style>
  