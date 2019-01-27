<template>
<div class="container">
      <ul>
        <li v-for="error in errors">{{ error }}</li>
      </ul>
  <input v-model="query" @keyup.enter="getBooks"/>
  <button id="submit" @click="getBooks" > Submit </button> 

  <div class="result" v-for="book in books">
    <div id="pic">
    <p><img v-bind:src="book.volumeInfo.imageLinks['thumbnail']" alt=""></p>  
    <p v-if="!book.volumeInfo.imageLinks['thumbnail']">No Image</p>
    </div>
    <div id="info">   
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
        errors: [],
        books: [],
        query: ''
      };
    },
    created: function() {},
    methods: {
      getBooks() {
        if (!this.query) {
          window.alert("ENTRY CANNOT BE BLANK");
        }

        axios
          .get(`https://www.googleapis.com/books/v1/volumes?q=${this.query}`)
          .then(response => {
            this.books = response.data.items;
          }).catch(error => {
            this.errors = error.response.data.errors;
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