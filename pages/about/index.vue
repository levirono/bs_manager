<template>
    <div>
      <h2 class="text-3xl font-bold mb-4 text-gray-800 dark:text-white">About Us</h2>
      
      <UCard class="mb-4 bg-orange-50 border-orange-200 dark:bg-orange-900 dark:border-orange-700">
        <template #header>
          <h3 class="text-xl font-semibold text-orange-800 dark:text-orange-200">Our Mission</h3>
        </template>
        <p class="text-gray-700 dark:text-gray-300">
          Our mission is to provide high-quality products and exceptional service to our customers while maintaining transparent and efficient business operations.
        </p>
      </UCard>
  
      <UCard class="mb-4 bg-green-50 border-green-200 dark:bg-green-900 dark:border-green-700">
        <template #header>
          <h3 class="text-xl font-semibold text-green-800 dark:text-green-200">Key Features</h3>
        </template>
        <ul class="list-disc list-inside text-gray-700 dark:text-gray-300">
          <li>Efficient inventory management</li>
          <li>Real-time profit analysis</li>
          <li>User-friendly sales tracking</li>
          <li>Customizable product pricing</li>
        </ul>
      </UCard>
  
      <UCard class="bg-gray-50 border-gray-200 dark:bg-gray-900 dark:border-gray-700">
        <template #header>
          <h3 class="text-xl font-semibold text-gray-800 dark:text-gray-200">Contact Us</h3>
        </template>
        <p class="text-gray-700 dark:text-gray-300">
          For any inquiries or support, please contact us at:
        </p>
        <p class="text-gray-700 dark:text-gray-300 font-bold mt-2">
          Email: support@ourbusiness.com<br>
          Phone: (555) 123-4567
        </p>
      </UCard>
    </div>
  </template>
  
  <script setup lang="ts">
  // No setup logic needed for this page currently
  </script>
  