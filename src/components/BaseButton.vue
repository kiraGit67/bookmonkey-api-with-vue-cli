<template>
  <button :class="cssButtonStyle">{{ buttonText }}</button>
</template>

<script>
export default {
  name: "BaseButton",
  props: {
    buttonText: String,
    variant: {
      type: String,
      default: "primary",
    },
  },
  computed: {
    cssButtonStyle() {
      return `${this.variant}-button`;
    },
  },
};
</script>

<style scoped>
button {
  font-size: 1.25rem;
  padding: 0.5rem 0.75rem;
  border: 2px solid grey;
  color: grey;
  background-color: transparent;
}

.primary-button {
  border: 2px solid #42b983;
  color: #42b983;
}

.primary-button:hover {
  background-color: #42b983;
  color: white;
}

.secondary-button {
  border: 2px solid darkcyan;
  color: darkcyan;
}

.secondary-button:hover {
  background-color: darkcyan;
  color: white;
}
</style>
