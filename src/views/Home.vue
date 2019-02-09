<template>
<div class="container">
  <h1>Page Turners </h1>
  <p>By Karim Shakir</p>
  <p v-if="errors">{{ errors }}</p>
  <div class="input-group input-group-sm mb-3">
    <div class="input-group-prepend">
      <span class="input-group-text" id="submit" @click="submitSearch">Submit</span>
    </div>
    <input v-model="query" @keyup.enter="submitSearch" type="text" class="form-control" aria-label="Sizing example 
            input" aria-describedby="inputGroup-sizing-sm">
  </div>
  <p v-if="message">{{ message }}</p>
  <div v-for="book in books">
    <div class="result" id="pic">
      <p v-if="!book.volumeInfo.imageLinks">No Image</p>
      <p v-if="book.volumeInfo.imageLinks">
        <img v-bind:src="book.volumeInfo.imageLinks['thumbnail']" alt="">
      </p>  
    </div>
    <div class="result" id="info">   
      <p div v-if="!book.volumeInfo.authors"> No Author </p>
      <p v-if="book.volumeInfo.authors" v-for="author in book.volumeInfo.authors">Author: {{ author }}</p>
      <p v-if="!book.volumeInfo.title"> No Title </p>
      <p v-if="book.volumeInfo.title"> Title:  {{ book.volumeInfo.title }}</p>
      <p v-if="!book.volumeInfo.publisher"> No Publisher</p> 
      <p v-if="book.volumeInfo.publisher"> Publisher:  {{ book.volumeInfo.publisher }}</p>
      <a v-bind:href="'https://books.google.com/books?id=' + book.id"> More Info </a>
    </div>
  </div>    
</div>
</template>

<style>
</style>

<script>
  const axios = require('axios');
  export default {
    data: function() {
      return {
        errors: '',
        books: [],
        query: '',
        message: ''
      };
    },
    created: function() {},
    methods: {
      submitSearch() {
        this.validateEntry();
        this.getBooks();
        this.resetData();
      },
      validateEntry() {
        if (!this.query) {
          alert("ENTRY CANNOT BE BLANK");
          return;
        }
      },
      getBooks() {
        axios
          .get(`https://www.googleapis.com/books/v1/volumes?q=${this.query}`)
          .then(response => {
            this.books = response.data.totalItems ? response.data.items : [];
            if (!this.books.length) {
              this.message = 'No results matching that search.';
            }
          }).catch(error => {
            this.errors = "Error making Request!";
          });
      },
      resetData() {
        this.errors = '';
        this.message = '';
        this.query = '';
      },
    },
    computed: {}
};
</script>