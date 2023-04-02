<template>
  <h1>{{ headline }}</h1>
  <p>{{ paragraph }}</p>
  <ul class="booklist">
    <li v-for="listItem in listItems" :key="listItem">
      <div class="cover">
        <img
          :src="listItem.cover"
          :alt="listItem.title"
          :title="listItem.title"
        />
      </div>
      <div class="details">
        <h2>{{ listItem.title }}</h2>
        <h3>
          {{ listItem.subtitle }} <br /><span> from {{ listItem.author }}</span>
        </h3>
        <p>{{ listItem.abstract }}</p>
        <ul class="inline-list">
          <li>{{ listItem.publisher }}</li>
          <li>ISBN: {{ listItem.isbn }}</li>
          <li>{{ listItem.price }}</li>
          <li>Count of Pages: {{ listItem.numPages }}</li>
        </ul>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: "BookMonkeyList",
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
};
</script>

<style scoped>
h1 {
  color: #42b983;
  text-shadow: 1px 1px 0px rgba(0, 0, 0, 0.15);
}

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
