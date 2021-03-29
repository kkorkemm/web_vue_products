<template>
  <div id="app">
    <h1>Учет товаров</h1>
    <AddProduct
      @add-product='addProduct'
    />
    <ProductTable
      v-if='products.length'
      v-bind:products='products'
      @remove-product='removeProduct'
    />
    <p v-else>Товаров нет!</p>
    <div class="productSumm">
      <p>Итоговая сумма: </p>
      <p>{{totalSum()}}</p>
    </div>
  </div>
</template>

<script>
import ProductTable from '@/components/Table/ProductTable'
import AddProduct from '@/components/AddProduct'

export default {
  name: 'App',
  data() {
    return {
      products: [
        {id: 1, title: 'Книга "Зеленая миля"', date: '2021-01-11', count: 1, price: 3000, summ: 3000},
        {id: 2, title: 'Телефон', date: '2021-01-11', count: 1, price: 40000, summ: 40000},
        {id: 3, title: 'Сумка', date: '2021-01-11', count: 2, price: 8000, summ: 16000}
      ]
    }
  },
  components: {
    ProductTable, AddProduct
  },
  methods: {
    removeProduct(id) {
      this.products = this.products.filter(p => p.id !== id)
    },
    addProduct(product) {
      this.products.push(product)
    }, 
    totalSum() {
      let sum = 0
      for (let i = 0; i < this.products.length; i++) {
        sum += this.products[i].summ;
      }
      return sum
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.productSumm {
  width: 80%;
  display: flex;
  justify-content: space-between;
  margin: 20px auto;
  padding: 0 10px;
  border: 2px solid rgb(3, 74, 141);
  border-radius: 10px;
  font-weight: bold;
}
</style>
