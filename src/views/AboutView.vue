<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="app">
    <ul id="example-1">
        <li>Book name: {{book.name}}</li>
        <br>
        <li>List of authors: {{book.authors}}</li>
        <br>
        <li>ISBN: {{book.isbn}}</li>
        <br>
        <li>Number of pages: {{book.numberOfPages}}</li>
        <br>
        <li>Published by {{book.publisher}}</li>
        <br>
        <li>Originally released in {{book.country}}</li>
        <br>
        <li>Number of characters: {{characterCount}}</li>
    </ul>
    <br>
    <br>
    <br>
    <router-link to="/">Back to home</router-link>
    <router-view />
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
import bookData from "@/dataForParsing.json";

export default {
  props: ['name'],
  name: "Details",

  data() {
    return { 
      book: {}, 
      characterCount: ''};
  },
  created() {
    for(let book of bookData)
    {
      if(book.name == localStorage.getItem("requestedBook")){
        this.book = book;
      }
    }
    this.characterCount = this.book.characters.length;
  },
};
</script>
