<template>
  <div>
    <input @input="termChange" placeholder="Type to begin your search"/>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    termChange: function(event) {
      this.$emit("searchTermChange", event.target.value);
    }
  }
};
</script>

<style scoped>
input {
  width: 100%;
  height: 40px;
  padding: 10px;
}

div {
  margin: 20px;
}
</style>