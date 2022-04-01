<template>
  <div class="home">
    <ul id="example-1">
      <li v-for="book in this.simpleBookData" :key="book">
        Book: <router-link to="/details/name" @click="setBook(book.name)">{{ book.name }}</router-link>
        <br />
        First author: {{ book.authors }}
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
import axios from "axios";

export default {
  name: "HomeView",
  components: {},
  data() {
    return { simpleBookData: [] };
  },
  methods: {
    async getData() {
      try {
        const response = await axios.get(
          "http://cantab.elaclo.com:8000/books.json"
        );
        this.simpleBookData = response.data;
      } catch (error) {
        console.log(error);
      }
    },
    consolePrintData() {
      console.log(this.simpleBookData);
    },
    setBook(name) {
      localStorage.setItem("requestedBook", name);
    },
  },

  created() {
    this.getData();
    this.consolePrintData();
  },
};
</script>
