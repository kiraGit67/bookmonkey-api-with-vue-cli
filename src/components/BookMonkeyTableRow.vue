<template>
  <tr>
    <td class="title-cell">
      <strong>{{ title }}</strong
      ><br />{{ subtitle }}
    </td>
    <td>{{ author }}</td>
    <td>{{ publisher }}</td>
    <td>{{ isbn }}</td>
    <td>
      <base-button
        :buttonText="baseButtonText"
        :variant="baseButtonStyle"
        @button-clicked="handleBookmarkButtonClick"
      />
    </td>
  </tr>
</template>

<script>
import BaseButton from "@/components/BaseButton.vue";

export default {
  components: {
    BaseButton,
  },
  props: {
    title: String,
    subtitle: String,
    author: String,
    publisher: String,
    isbn: String,
    isBookmarked: Boolean,
  },
  computed: {
    baseButtonText() {
      return this.isBookmarked ? "Remove Bookmark" : "Add Bookmark";
    },
    baseButtonStyle() {
      return this.isBookmarked ? "primary" : "secondary";
    },
  },
  methods: {
    handleBookmarkButtonClick() {
      this.$emit("bookmark-clicked", this.isbn);
    },
  },
};
</script>

<style scoped>
td {
  width: 15%;
  padding: 5px 10px 5px 0;
  margin-inline: 0;
  margin-bottom: 5px;
  border-bottom: 1px solid lightgrey;
  vertical-align: top;
}

td.title-cell {
  width: 40%;
}

td > strong {
  color: darkcyan;
}

button {
  padding: 0.25rem;
  font-size: 1rem;
}
</style>
