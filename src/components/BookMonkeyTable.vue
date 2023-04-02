<template>
  <section>
    <h2>{{ headline }}</h2>
    <table>
      <thead>
        <tr>
          <th class="title-cell">Title</th>
          <th>Author</th>
          <th>Publisher</th>
          <th>ISBN</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <book-monkey-table-row
          v-for="bookItem in bookList"
          :key="bookItem.isbn"
          :title="bookItem.title"
          :subtitle="bookItem.subtitle"
          :author="bookItem.author"
          :publisher="bookItem.publisher"
          :isbn="bookItem.isbn"
          :isBookmarked="bookItem?.isBookmarked"
          @bookmark-clicked="handleBookmarkClick"
        />
      </tbody>
    </table>
  </section>
</template>

<script>
import BookMonkeyTableRow from "@/components/BookMonkeyTableRow.vue";

export default {
  name: "BookMonkeyTable",
  components: {
    BookMonkeyTableRow,
  },
  props: {
    headline: String,
    bookList: Array,
  },
  methods: {
    handleBookmarkClick(isbn) {
      const currentBookIndex = this.bookList.findIndex(
        (bookItem) => bookItem.isbn === isbn
      );
      const currentBookItem = this.bookList[currentBookIndex];
      currentBookItem.isBookmarked = !currentBookItem.isBookmarked
        ? true
        : false;
    },
  },
};
</script>

<style scoped>
table {
  width: 100%;
  border: none;
}

th {
  width: 15%;
  background-color: darkcyan;
  color: white;
  padding: 0.25rem 0.15rem;
}

th.title-cell {
  width: 40%;
}
</style>
