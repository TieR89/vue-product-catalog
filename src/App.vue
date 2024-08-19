<template>
  <div id="app" :class="{ wide: isWideScreen, medium: isMediumScreen }">
    <header>
      <div class="logo">Логотип</div>
      <nav>
        <ul>
          <li><a href="#" class="active">Каталог</a></li>
          <search-bar :is-mobile="isMobileScreen"></search-bar>
          <li v-if="!isMobileScreen"><a href="#">Информация о компании</a></li>
          <li v-if="!isMobileScreen"><a href="#">Контакты</a></li>
          <li v-if="!isMobileScreen"><a href="#">Полезные ссылки</a></li>
        </ul>
      </nav>
    </header>

    <main>
      <sidebar v-if="!isMobileScreen"></sidebar>
      <product-grid :products="products"></product-grid>
    </main>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import Sidebar from './components/Sidebar.vue';
import ProductGrid from './components/ProductGrid.vue';

export default {
  name: 'App',
  components: {
    SearchBar,
    Sidebar,
    ProductGrid,
  },
  data() {
    return {
      products: [
        {
          id: 1,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
        {
          id: 2,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
        {
          id: 3,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
        {
          id: 4,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
        {
          id: 5,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
        {
          id: 6,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
        {
          id: 7,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
        {
          id: 8,
          brand: 'Бренд',
          name: 'Полное название товара в несколько строк для вида с обрывом в конце...',
          price: 5990,
          oldPrice: 7990,
          discount: 25,
          isBestseller: true,
        },
      ],
    };
  },
  computed: {
    isWideScreen() {
      return window.innerWidth >= 1920;
    },
    isMediumScreen() {
      return window.innerWidth >= 1440 && window.innerWidth < 1920;
    },
    isMobileScreen() {
      return window.innerWidth < 768; 
    },
  },
  mounted() {
    window.addEventListener('resize', this.handleResize);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.handleResize);
  },
  methods: {
    handleResize() {
      this.$forceUpdate();
    },
  },
};
</script>

<style lang="scss" scoped>
@import './styles/variables.scss';

body {
  font-family: Arial, sans-serif;
  color: $text-color;
  margin: 0;
  padding: 0;
}

#app {
  max-width: 100%;
  margin: 0 auto;

  &.wide {
    max-width: 1720px;
  }

  &.medium {
    max-width: 1240px;
  }
}

header {
  display: flex;
  align-items: center;
  padding: 1rem;
  border-bottom: 1px solid $border-color;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
}

.active {
  padding: 1rem;
  border: 1px solid $primary-color;
  border-radius: 9px;
}

nav {
  width: 100%;
}

nav ul {
  display: flex;
  justify-content: space-between;
  list-style-type: none;
  align-items: center;
  width: 100%;
  flex-grow: 1;
  padding: 0;
}

nav ul li {
  margin-right: 1rem;
  text-align: center;
}

nav ul li a {
  text-decoration: none;
  color: $text-color;
}

nav ul li a:hover {
  text-decoration: underline;
}

.search-container {
  flex-grow: 1;
}

main {
  display: flex;
  padding: 1rem;
}

@media (max-width: 1440px) {
  nav ul {
    justify-content: flex-end;
  }
}

@media (max-width: 768px) {
  header {
    flex-direction: column;
    align-items: flex-start;
  }

  nav ul {
    flex-direction: column;
    margin-top: 1rem;
  }

  nav ul li:not(:nth-child(2)) {
    display: none;
  }

  main {
    flex-direction: column;
  }

  .logo {
    display: none;
  }
}
</style>
