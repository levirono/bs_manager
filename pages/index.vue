<template>
    <div class="text-center px-4 sm:px-6 lg:px-8">
      <h1 class="text-3xl sm:text-4xl lg:text-5xl font-bold mb-4">Welcome to the Business Management Dashboard</h1>
      <p class="text-lg sm:text-xl text-gray-700 mb-8">
        Manage your business effectively with our comprehensive platform. Track sales, monitor inventory, and analyze profits with ease, all in one place.
      </p>
      
      <div class="flex flex-col sm:flex-row justify-around mb-8 space-y-4 sm:space-y-0 sm:space-x-4">
        <div class="bg-white rounded-lg p-4 shadow-md w-full sm:w-1/3">
          <h2 class="text-green-600 text-xl font-semibold mb-2">Sales Management</h2>
          <p class="text-gray-600">Track sales in real-time, monitor customer orders, and generate detailed sales reports to optimize performance.</p>
        </div>
  
        <div class="bg-white rounded-lg p-4 shadow-md w-full sm:w-1/3">
          <h2 class="text-green-600 text-xl font-semibold mb-2">Inventory Control</h2>
          <p class="text-gray-600">Keep an eye on stock levels, manage product listings, and ensure your inventory is always up-to-date.</p>
        </div>
  
        <div class="bg-white rounded-lg p-4 shadow-md w-full sm:w-1/3">
          <h2 class="text-green-600 text-xl font-semibold mb-2">Profit Analysis</h2>
          <p class="text-gray-600">Analyze your business performance by tracking profits across different products and time periods.</p>
        </div>
      </div>
      
      <UButton color="orange" label="Learn More" />
    </div>
  </template>