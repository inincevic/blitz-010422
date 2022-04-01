<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="app">
    <ul id="example-1" v-if="book.name">
        <li>{{book.name}}</li>
    </ul>
  </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Details",
  props: ["name"],

  data() {
    return { book: {} };
  },
  methods: {
    async getBookData() {
      try {
        const response = await axios.get(
          "http://cantab.elaclo.com:8000/books.json"
        );
        return response.data;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.getBookData().then((data) => {
      this.book = data.find(
        (book) => book.name === localStorage.getItem("requestedName")
      );
      console.log(this.commit);
    });
  },
};
</script>
