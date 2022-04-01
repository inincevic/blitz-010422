<template>
  <div class="home">
    <ul id="example-1">
      <li v-for="book in this.bookData" :key="book">
        Book: <router-link to="/about/name" @click="setBook(book.name)">{{ book.name }}</router-link>
        <br />
        First author: {{ book.authors[0] }}
        <br />
        Release date: {{ book.released }}

        <br />
        <br />
      </li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import bookData from "@/dataForParsing.json";

export default {
  name: "HomeView",
  components: {},
  data() {
    return { 
      bookData,
     };
  },
  methods: {
    setBook(name) {
      localStorage.setItem("requestedBook", name);
    },
  },
};
</script>
