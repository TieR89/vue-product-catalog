<template>
  <div class="product-card">
    <div class="product-image">
      <img src="../img/box.svg" alt="Product" />
      <span class="bestseller" v-if="product.isBestseller">Хит продаж 🔥</span>
      <span class="discount" v-if="product.discount">
        {{ product.discount }}%
      </span>
    </div>
    <div class="product-info">
      <h4>{{ product.brand }}</h4>
      <p>{{ product.name }}</p>
      <div class="product-price">
        <span class="current-price">{{ product.price }} ₽</span>
        <span class="old-price" v-if="product.oldPrice">
          {{ product.oldPrice }} ₽
        </span>
      </div>
      <button class="buy-button">В корзину</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
@import '../styles/variables.scss';

.product-card {
  border: 1px solid $border-color;
  border-radius: 4px;
  overflow: hidden;
  height: 400px;
}

.product-image {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $secondary-color;
  height: 200px;
}

.product-image img {
  max-width: 100%;
  max-height: 100%;
}

.bestseller {
  position: absolute;
  top: 0.5rem;
  left: 0.5rem;
  background-color: white;
  color: $text-color;
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
  font-size: 0.8rem;
}

.discount {
  position: absolute;
  bottom: 0.5rem;
  left: 0.5rem;
  background-color: $primary-color;
  color: white;
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
  font-size: 0.8rem;
}

.product-info {
  padding: 1rem;
}

.product-info h4 {
  margin: 0 0 0.5rem;
}

.product-info p {
  margin: 0 0 1rem;
  font-size: 0.9rem;
}

.product-price {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.current-price {
  font-weight: bold;
  font-size: 1.1rem;
  margin-right: 0.5rem;
}

.old-price {
  text-decoration: line-through;
  color: #5f6368;
  font-size: 0.9rem;
}

.buy-button {
  width: 100%;
  padding: 0.5rem;
  background-color: $primary-color;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.buy-button:hover {
  background-color: #3367d6;
}
</style>
