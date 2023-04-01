<template>
  <book-monkey-list
    headline="All BookMonkey Books"
    paragraph="A list of all the books from the API"
    :listItems="books"
  />
</template>

<script>
import BookMonkeyList from "@/components/BookMonkeyList.vue";

export default {
  name: "App",
  components: {
    BookMonkeyList,
  },
  data() {
    return {
      books: [],
    };
  },
  async created() {
    const response = await fetch("http://localhost:4730/books");
    this.books = await response.json();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
  padding: 0 3rem 4rem 3rem;
}
</style>
