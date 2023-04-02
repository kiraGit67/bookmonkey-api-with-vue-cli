<template>
  <li>
    <div class="cover">
      <img :src="cover" :alt="title" :title="title" />
      <base-button
        :buttonText="bookmarkButtonText"
        :variant="bookmarkButtonStyle"
        @button-clicked="bookmarkButtonClick"
      />
    </div>
    <div class="details">
      <h2>{{ title }}</h2>
      <h3>
        {{ subtitle }} <br /><span> from {{ author }}</span>
      </h3>
      <p>{{ abstract }}</p>
      <ul class="inline-list">
        <li>{{ publisher }}</li>
        <li>ISBN: {{ isbn }}</li>
        <li>{{ price }}</li>
        <li>Count of Pages: {{ numPages }}</li>
      </ul>
    </div>
  </li>
</template>

<script>
import BaseButton from "@/components/BaseButton.vue";

export default {
  components: {
    BaseButton,
  },
  props: {
    cover: String,
    title: String,
    subtitle: String,
    author: String,
    abstract: String,
    publisher: String,
    isbn: String,
    price: String,
    numPages: Number,
    isBookmarked: Boolean,
  },
  computed: {
    bookmarkButtonText() {
      return this.isBookmarked ? "Remove Bookmark" : "AddBookmark";
    },
    bookmarkButtonStyle() {
      return this.isBookmarked ? "primary" : "secondary";
    },
  },
  methods: {
    bookmarkButtonClick() {
      this.$emit("bookmark-clicked", this.isbn);
    },
  },
};
</script>

<style scoped>
.booklist {
  list-style-type: none;
  padding-left: 0;
}
.booklist > li {
  display: grid;
  grid-template-columns: 1fr 3fr;
  padding-bottom: 1.5rem;
  margin-bottom: 2.5rem;
  border-bottom: 1px solid #42b983;
}
.booklist > li img {
  margin-left: 0;
}
.booklist > li h2 {
  font-weight: normal;
  color: #42b983;
}
.booklist > li h3 {
  font-weight: normal;
  color: #2c3e50;
}
.inline-list {
  list-style-type: none;
  padding-left: 0;
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
}
.inline-list li::before {
  content: "";
  background-color: #42b983;
  width: 10px;
  height: 10px;
  border: none;
  border-radius: 100%;
  display: inline-block;
  margin-right: 0.5rem;
}
p {
  color: black;
}

@media screen and (max-width: 767px) {
  .booklist > li {
    display: grid;
    grid-template-columns: 1fr;
  }
}
</style>
