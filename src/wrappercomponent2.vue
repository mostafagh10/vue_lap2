<template>
    <div>
      <Banner @show-books="showBooks" @show-wishlist="showWishlist"></Banner>
      <component :is="currentView" :books="books" :wishlistItems="wishlist" @add-to-wishlist="addToWishlist" @remove-from-wishlist="removeFromWishlist"></component>
    </div>
  </template>
  
  <script>
  import Banner from '@/components/banner.vue';
  import BookList from '@/components/booksLists.vue';
  import Wishlist from '@/components/wishlist.vue';
  import books from './books.js';
  
  export default {
    components: {
      Banner,
      BookList,
      Wishlist
    },
    data() {
      return {
        currentView: 'BookList',
        books: [],
        wishlist: [] 
      };
    },
    methods: {
      showBooks() {
        this.currentView = 'BookList';
      },
      showWishlist() {
        this.currentView = 'Wishlist';
      },
      addToWishlist(book) {
        this.wishlist.push({ book });
      },
      removeFromWishlist(item) {
        const index = this.wishlist.findIndex(w => w.book.title === item.book.title);
        if (index !== -1) {
          this.wishlist.splice(index, 1);
        }
      }
    },
    mounted() {
      this.books = books;
    }
  };
  </script>
  
  <style>
  </style>
  