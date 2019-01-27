<template>
<div class="container">
  <input v-model="query" @keyup.enter="getBooks"/>
  <button id="submit" @click="getBooks" > Submit </button> 

  <div class="result" v-for="book in books">
    <div>
    <p><img id="pic" v-bind:src="book.volumeInfo.imageLinks['thumbnail']" alt=""></p>  
    </div>
    <div>   
    <p v-if="!book.volumeInfo.imageLinks['thumbnail']">No Image</p>
    <p v-if="book.volumeInfo.authors" v-for="author in book.volumeInfo.authors">Author: {{author}}</p>
    <p div v-if="!book.volumeInfo.authors"> No Author </p>
    <p v-if="book.volumeInfo.title"> Title:  {{ book.volumeInfo.title }}</p>
    <p v-if="!book.volumeInfo.title"> No Title </p>
    <p v-if="book.volumeInfo.publisher"> Publisher:  {{ book.volumeInfo.publisher }}</p>
    <p v-if="!book.volumeInfo.publisher"> No Publisher</p> 
    <a v-bind:href="'https://books.google.com/books?id=' + book.id">More Info</a>
    </div>
  </div>    
</div>
</template>


<style>
</style>

<script>
  var axios = require('axios');
  export default {
    data: function() {
      return {
        // errors: [],
        books: [],
        query: ''
      };
    },
    created: function() {},
    methods: {
      getBooks() {
        axios
          .get(`https://www.googleapis.com/books/v1/volumes?q=${this.query}`)
          .then(response => {
            this.books = response.data.items;
          });
        this.query = "";
      },
      clearEntry: function() {
        document.getElementById("myForm").reset();
      }
    },
    computed: {}
};

</script>