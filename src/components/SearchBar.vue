<template>
  <div class="search">
    <div class="search-icon"></div>
    <input
      type="text"
      placeholder="Поиск по 100 000 товаров"
      v-model="searchQuery"
    />
    <!-- <button @click="search">Найти</button> -->
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  data() {
    return {
      searchQuery: '',
    };
  },
  methods: {
    search() {
      console.log('Searching for:', this.searchQuery);
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../styles/variables.scss';

.search {
  display: flex;
  width: 100%;
  align-items: center;
}

.search input {
  flex-grow: 1;
  padding: 1rem;
  border: 1px solid $primary-color;
  border-radius: 9px;
  padding-left: 2rem;
}

.search button {
  padding: 0.5rem 1rem;
  background-color: $primary-color;
  color: white;
  border: none;
  border-radius: 0 4px 4px 0;
  cursor: pointer;
}

.search-icon {
  background-image: url('@/img/zoom.svg');
  background-size: contain;
  background-repeat: no-repeat;
  width: 30px;
  height: 30px;
  position: absolute;
  margin-left: 5px;
}

@media (max-width: 768px) {
  .search {
    width: 100%;
    margin-top: 1rem;
  }

  .search input {
    flex-grow: 1;
  }
}
</style>
