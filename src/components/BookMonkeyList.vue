<template>
  <h1>{{ headline }}</h1>
  <p>{{ paragraph }}</p>
  <ul class="booklist">
    <book-monkey-list-item
      v-for="listItem of listItems"
      :key="listItem.isbn"
      :cover="listItem.cover"
      :title="listItem.title"
      :subtitle="listItem.subtitle"
      :author="listItem.author"
      :abstract="listItem.abstract"
      :isbn="listItem.isbn"
      :publisher="listItem.publisher"
      :price="listItem.price"
      :numPages="listItem.numPages"
      :isBookmarked="listItem?.isBookmarked"
      @bookmark-clicked="bookmarkClick"
    />
  </ul>
</template>

<script>
import BookMonkeyListItem from "@/components/BookMonkeyListItem.vue";

export default {
  name: "BookMonkeyList",
  components: {
    BookMonkeyListItem,
  },
  props: {
    headline: String,
    paragraph: String,
    listItems: Array,
  },
  data() {
    return {
      buttonText: "Add Bookmark",
      buttonStyle: "primary",
    };
  },
  methods: {
    bookmarkClick(isbn) {
      const currentBookIndex = this.listItems.findIndex(
        (listItem) => listItem.isbn === isbn
      );
      const currentBook = this.listItems[currentBookIndex];
      currentBook.isBookmarked = !currentBook.isBookmarked ? true : false;
    },
  },
};
</script>

<style scoped>
h1 {
  color: #42b983;
  text-shadow: 1px 1px 0px rgba(0, 0, 0, 0.15);
}
</style>
