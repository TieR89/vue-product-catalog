<template>
  <aside>
    <div class="categories">
      <h3>Название категории</h3>
      <ul>
        <li>Название категории</li>
        <li>Название категории</li>
        <li class="active">Название категории</li>
      </ul>
    </div>
    <div class="price-filter">
      <h3>Цена</h3>
      <div class="price-inputs">
        <input type="number" placeholder="от 5 500 ₽" v-model="minPrice" />
        <span>_</span>
        <input type="number" placeholder="до 5 500 ₽" v-model="maxPrice" />
      </div>
    </div>
    <div class="brand-filter">
      <h3>Бренд</h3>
      <div class="brand-search">
        <input type="text" placeholder="Поиск" v-model="brandSearch" />
      </div>
      <ul>
        <li v-for="brand in filteredBrands" :key="brand">
          <label>
            <input type="checkbox" v-model="selectedBrands" :value="brand" />
            {{ brand }}
          </label>
        </li>
      </ul>
    </div>
    <div class="size-filter">
      <h3>Размер</h3>
      <ul>
        <li v-for="size in sizes" :key="size">
          <label>
            <input type="checkbox" v-model="selectedSizes" :value="size" />
            {{ size }}
          </label>
        </li>
      </ul>
    </div>
  </aside>
</template>

<script>
export default {
  name: 'Sidebar',
  data() {
    return {
      minPrice: null,
      maxPrice: null,
      brandSearch: '',
      brands: [
        'Атрибут 1',
        'Атрибут 2',
        'Атрибут 3',
        'Атрибут 4',
        'Атрибут 5',
        'Атрибут 6',
      ],
      selectedBrands: [],
      sizes: [
        'Атрибут 1',
        'Атрибут 2',
        'Атрибут 3',
        'Атрибут 4',
        'Атрибут 5',
        'Атрибут 6',
      ],
      selectedSizes: [],
    };
  },
  computed: {
    filteredBrands() {
      return this.brands.filter(brand =>
        brand.toLowerCase().includes(this.brandSearch.toLowerCase())
      );
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../styles/variables.scss';

aside {
  width: 250px;
  margin-right: 1rem;
}

aside h3 {
  margin-top: 1rem;
  margin-bottom: 0.5rem;
}

aside ul {
  list-style-type: none;
  padding-left: 0;
}

aside ul li {
  margin-bottom: 0.5rem;
}

aside ul li.active {
  color: $primary-color;
}

.price-inputs {
  display: flex;
  gap: 0.5rem;
}

.price-inputs input,
.brand-search input {
  width: 90%;
  padding: 0.5rem;
  border: 1px solid $border-color;
  border-radius: 4px;
}

aside input[type='checkbox'] {
  margin-right: 0.5rem;
}

@media (max-width: 768px) {
  aside {
    width: 100%;
    margin-right: 0;
    margin-bottom: 1rem;
  }
}
</style>
