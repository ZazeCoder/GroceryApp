<template>
  <div id="app" style="margin-top: 100px;">
    <h2 style="text-align: center;">Grocery App</h2>
    <div v-for="(data, i) in products" :key="i">
      <GroceryApp :itemName="data.itemName" :price="data.price" :count="data.count" :index="i" :key="i"
        @addToCart="addCart" @remove="removeItem" />
    </div>
    <h4 style="font-family: sans-serif; font-size: 30px; font-style: bolder;">Total products: {{ counts }} </h4>
    <h4  style="font-family: sans-serif; font-size: 20px;" >Total Price: {{ rate }} </h4>
    <button class="btn" @click="emptyCart()">Empty Cart</button>
  </div>
</template>

<script>
import GroceryApp from './components/GroceryApp.vue'

export default {
  name: 'App',
  data() {
    return {
      products: [
        {
          itemName: 'Apple', price: 5, count: 0
        },
        {
          itemName: 'Mango', price: 10, count: 0
        },
        {
          itemName: 'Banana', price: 15, count: 0
        },
        {
          itemName: 'Papaya', price: 20, count: 0
        }
      ],
      counts: 0,
      rate: 0
    }
  },
  components: {
    GroceryApp
  },
  methods: {
    addCart(i) {
      // this.count += 1
      this.counts += 1
      this.products[i].count += 1
      this.rate += this.products[i].price
      // this.products[i].price += this.products[i].price

    },
    removeItem(i) {
      this.counts -= 1
      this.products[i].count -= 1
      if (this.products[i].count < 0) {
        this.products[i].count = 0
        this.rate = 0
        this.counts = 0

      }

    },
    emptyCart() {
      this.counts = 0
      this.rate = 0
      this.products.forEach(values => {
        values.count = 0
      });

    }
  }
}
</script>

<style>
.btn {
  background-color: rgb(18, 199, 175);
  font-size: 20px;
  font-family: sans-serif;
  border: none;
  border-radius: 5px;
  padding: 10px;
  font-weight: bolder;
}
.btn:hover {
  background-color: rgb(0, 173, 150);
  font-size: 20px;
  font-family: sans-serif;
  border: none;
  border-radius: 5px;
  padding: 10px;
  font-weight: bolder;
}

</style>
