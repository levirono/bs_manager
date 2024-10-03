<template>
    <div>
      <h2 class="text-3xl font-bold mb-4 text-gray-800">Sales Dashboard</h2>
      
      <!-- Record Sale -->
      <div class="w-full lg:w-1/2 mb-4 mx-auto">
        <UCard class="bg-orange-50 border-orange-200">
          <template #header>
            <h3 class="text-xl font-semibold text-orange-800">Record Sale</h3>
          </template>
          <UForm :state="formState" @submit="onSubmit">
            <UFormGroup label="Product" name="product">
              <!-- Make the select searchable -->
              <USelect
                v-model="formState.product"
                :options="filteredProductOptions"
                @search="onSearch"
                searchable
              />
            </UFormGroup>
            <UFormGroup label="Quantity" name="quantity">
              <UInput v-model="formState.quantity" type="number" />
            </UFormGroup>
            <UFormGroup label="Total Price" name="totalPrice">
              <UInput :model-value="totalPrice" readonly />
            </UFormGroup>
            <UButton type="submit" label="Record Sale" color="green" />
          </UForm>
        </UCard>
      </div>
  
      <!-- Today's Sales Summary -->
      <div class="w-full lg:w-1/2 mb-4 mx-auto">
        <UCard class="bg-blue-50 border-blue-200">
          <template #header>
            <h3 class="text-xl font-semibold text-blue-800">Today's Sales</h3>
          </template>
          <p class="text-lg text-gray-700">Total Sales Today: {{ totalSalesToday }}</p>
        </UCard>
      </div>
    
      <!-- Cumulative Sales Summary -->
      <div class="w-full lg:w-1/2 mb-4 mx-auto">
        <UCard class="bg-green-50 border-green-200">
          <template #header>
            <h3 class="text-xl font-semibold text-green-800">Cumulative Sales</h3>
          </template>
          <p class="text-lg text-gray-700">Total Cumulative Sales: {{ cumulativeSales }}</p>
        </UCard>
      </div>
  
      <!-- Sales History -->
      <div class="w-full lg:w-1/2 mx-auto">
        <UCard class="bg-gray-50 border-gray-200">
          <template #header>
            <h3 class="text-xl font-semibold text-gray-800">Sales History</h3>
          </template>
          <UTable :columns="columns" :rows="sales" />
        </UCard>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
import { ref, computed } from 'vue'

const formState = ref({
  product: null,
  quantity: 1,
})

const productOptions = ref([
  { label: 'Product A', value: 'a', price: 10 },
  { label: 'Product B', value: 'b', price: 20 },
])

const sales = ref([
  { product: 'Product A', quantity: 2, total: 20, date: new Date().toISOString().slice(0, 10) },
  { product: 'Product B', quantity: 1, total: 20, date: new Date().toISOString().slice(0, 10) },
])

const columns = [
  { key: 'product', label: 'Product' },
  { key: 'quantity', label: 'Quantity' },
  { key: 'total', label: 'Total' },
]

// Filtered product options for searchable dropdown
const searchQuery = ref("")
const filteredProductOptions = computed(() => {
  if (!searchQuery.value) return productOptions.value
  return productOptions.value.filter((product) =>
    product.label.toLowerCase().includes(searchQuery.value.toLowerCase())
  )
})

// Compute total price based on selected product and quantity
const totalPrice = computed(() => {
  const selectedProduct = productOptions.value.find(
    (p) => p.value === formState.value.product
  )
  return selectedProduct ? selectedProduct.price * formState.value.quantity : 0
})

// Submit the sale and add to sales history
const onSubmit = () => {
  if (formState.value.product && formState.value.quantity) {
    const newSale = {
      product: formState.value.product,
      quantity: formState.value.quantity,
      total: totalPrice.value,
      date: new Date().toISOString().slice(0, 10), // Current date in YYYY-MM-DD format
    }

    sales.value.push(newSale)
    console.log("Sale recorded:", newSale)

    // Reset form after submission
    formState.value.product = null
    formState.value.quantity = 1
  } else {
    console.error("Product or quantity is undefined!")
  }
}

// Filter sales for today
const today = new Date().toISOString().slice(0, 10)
const totalSalesToday = computed(() => {
  return sales.value
    .filter(sale => sale.date === today)
    .reduce((acc, sale) => acc + sale.total, 0)
})

// Compute cumulative sales (all-time total)
const cumulativeSales = computed(() => {
  return sales.value.reduce((acc, sale) => acc + sale.total, 0)
})

// Search function for searchable product dropdown
const onSearch = (query: string) => {
  searchQuery.value = query
}
</script>
