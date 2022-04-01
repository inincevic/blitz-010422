<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="app">
    <ul id="example-1">
        <li>{{book.name}}</li>
        <br>
        <li>{{book.authors}}</li>
        <br>
        <li>{{book.isbn}}</li>
        <br>
        <li>{{book.numberOfPages}}</li>
        <br>
        <li>{{book.publisher}}</li>
        <br>
        <li>{{book.country}}</li>
        <br>
        <li>{{characterCount}}</li>
    </ul>
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
