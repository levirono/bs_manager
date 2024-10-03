<template>
    <div>
      <h2 class="text-3xl font-bold mb-4 text-gray-800">Your Inventory</h2>
      
      <!-- Set Initial and Sale Prices -->
      <UCard class="mb-4 bg-orange-50 border-orange-200">
        <template #header>
          <h3 class="text-xl font-semibold text-orange-800">Set Prices</h3>
        </template>
        <UForm :state="formState" @submit="onSubmit">
          <UFormGroup label="Product Name" name="productName">
            <UInput v-model="formState.productName" />
          </UFormGroup>
          <UFormGroup label="Initial Price" name="initialPrice">
            <UInput v-model="formState.initialPrice" type="number" />
          </UFormGroup>
          <UFormGroup label="Sale Price" name="salePrice">
            <UInput v-model="formState.salePrice" type="number" />
          </UFormGroup>
          <UButton type="submit" label="Set Price" color="orange" />
        </UForm>
      </UCard>
      
      <!-- Product List with Profit -->
      <UCard class="bg-green-50 border-green-200">
        <template #header>
          <h3 class="text-xl font-semibold text-green-800">Product List</h3>
        </template>
        <UTable :columns="columns" :rows="products" />
      </UCard>
    </div>
  </template>

<script setup lang="ts">
import { ref } from 'vue'

const formState = ref({
  productName: '',
  initialPrice: 0,
  salePrice: 0,
})

const products = ref([
  { name: 'Product A', initialPrice: 10, salePrice: 15 },
  { name: 'Product B', initialPrice: 20, salePrice: 30 },
])

// Columns including profit calculation
const columns = [
  { key: 'name', label: 'Product Name' },
  { key: 'initialPrice', label: 'Initial Price' },
  { key: 'salePrice', label: 'Sale Price' },
  { key: 'profit', label: 'Profit' },
]

const onSubmit = () => {
  const newProduct = {
    name: formState.value.productName,
    initialPrice: formState.value.initialPrice,
    salePrice: formState.value.salePrice,
    profit: formState.value.salePrice - formState.value.initialPrice,
  }

  products.value.push(newProduct)
  console.log('Form submitted:', newProduct)
}
</script>
