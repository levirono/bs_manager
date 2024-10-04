<template>
    <header class="py-4 px-4 md:px-8 bg-white dark:bg-gray-800">
      <div class="flex justify-between items-center">
        <div class="text-2xl font-bold text-gray-800 dark:text-white">
          BS-M
        </div>
  
        <div class="flex items-center">
          <UHorizontalNavigation :links="navigationLinks" class="justify-center mr-4">
          <template #default="{ link }">
            <span class="text-lg font-medium text-gray-700 dark:text-gray-300 hover:text-gray-900 dark:hover:text-white transition-colors duration-200">{{ link.label }}</span>
          </template>
        </UHorizontalNavigation>
        </div>
      </div>
    </header>
  </template>
  
  <script setup lang="ts">
  const navigationLinks = [
    { label: 'Home', to: '/' },
    { label: 'Inventory', to: '/inventory' },
    { label: 'Sales', to: '/sales' },
    { label: 'Profits', to: '/profits' },
    { label: 'About', to: '/about' },
  ];
  </script>
  