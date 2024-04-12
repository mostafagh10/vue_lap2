<template>
    <div class="d-flex align-items-baseline justify-content-between p-2 m-2" v-if="wishlistItems.length > 0">
      <div class="w-100">
        <table class="w-100 table-bordered table-striped text-center">
          <thead>
            <tr>
              <th>Author</th>
              <th>Country</th>
              <th>Language</th>
              <th>Pages</th>
              <th>Title</th>
              <th>Year</th>
              <th>Price</th>
              <th>Remove</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in wishlistItems" :key="item.book.title">
              <td>{{ item.book.author }}</td>
              <td>{{ item.book.country }}</td>
              <td>{{ item.book.language }}</td>
              <td>{{ item.book.pages }}</td>
              <td>{{ item.book.title }}</td>
              <td>{{ item.book.year }}</td>
              <td>{{ item.book.price }}</td>
              <td><button class="btn btn-danger" @click="removeFromWishlist(item)">Delete</button></td>
            </tr>
          </tbody>
        </table>
        <hr />
        <p class="text-success text-center">Total Price: {{ getTotalPrice() }}</p>
      </div>
    </div>
    <div v-else>
      <h4 class="text-danger text-center">Sorry, no books added to the wishlist.</h4>
    </div>
  </template>
  
  <script>
  export default {
    props: ['wishlistItems'],
    methods: {
      removeFromWishlist(item) {
        this.$emit('remove-from-wishlist', item);
      },
      getTotalPrice() {
        return this.wishlistItems.reduce((total, item) => total + Number(item.book.price), 0);
      }
    }
  };
  </script>
  
  <style>

  </style>
  