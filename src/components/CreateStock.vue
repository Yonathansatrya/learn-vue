<script setup>
import { reactive } from 'vue'

const emit = defineEmits(['add-stock-quantity'])

const stock = reactive({
  quantity: null
})

const onSubmit = () => {
  if (stock.quantity === null) {
    alert('Silahkan di isi dengan lengkap.')
    return
  }

  const AddStock = {
    quantity: stock.quantity,
  }
  emit('add-stock-quantity', AddStock)

  stock.quantity = null
}
</script>

<template>
  <form class="review-form" @submit.prevent="onSubmit">
   <label for="quantity">Add Stock</label>
    <input type="number" id="quantity" v-model="stock.quantity" min="0">
    <input class="button-submit" type="submit" value="Submit">
  </form>
</template>