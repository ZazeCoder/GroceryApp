<template>
  <div>

    <div class="root">
      <div class="left">
        <div class="left1">
          <p>{{ itemName }}</p>
          <p>Price: ${{ price }}</p>
          
        </div>
        <div class="left2">
          <button class="btn" @click="$emit('addToCart', index)">Add to cart</button>
        </div>
      </div>


      <div v-if="count > 0 " class="right">
        <div class="right1">
          <p>{{ itemName }}</p>
         
          <p>Quantity: {{ count }}</p>
        </div>
        <div class="left2">
          <button class="btn" @click="$emit('remove', index)">Remove from cart</button>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GroceryApp',
  props: [
    'price', 'itemName', 'count', 'index'

  ]
}
</script>

<style >
.root {
  display: flex;
  width: 100%;
  align-items: center;
  
  /* justify-content: center; */
}

.left,
.right {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 50%;
  border: 1px solid rgb(0, 0, 0);
  padding: 10px;
}

.right {
  display: flex;
  align-items: center;
  justify-content: space-around;
  width: 50%;
  border: 1px solid rgb(0, 0, 0);
}
</style>
