<template>
  <div class="search-bar">
    <label class="search-bar__title">{{ title }}</label>
    <input v-model="searchQuery" @input="onSearch" type="text" placeholder="Поиск..." class="search-bar__input" />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  props: {
    onSearch: Function,
    title: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      searchQuery: "",
    };
  },
  watch: {
    searchQuery(value) {
      this.onSearch(value);
    },
  },
};
</script>

<style scoped>
.search-bar {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
}

.search-bar__title {
  font-size: 1rem;
  margin-bottom: 5px;
  color: #333;
  font-weight: 300;
  text-align: left;
}

.search-bar__input {
  padding: 10px;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 10px;
  font-size: 16px;
}
</style>
