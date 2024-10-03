<template>
    <div class="min-h-screen bg-gray-100">
      <UContainer>
        <UHeader>
          <template #left>
            <h1 class="text-2xl font-bold">Business App</h1>
          </template>
          <template #right>
            <UButton to="/" label="Home" />
            <UButton to="/admin" label="Admin" />
            <UButton to="/sales" label="Sales" />
          </template>
        </UHeader>
        <main class="py-8">
          <slot />
        </main>
      </UContainer>
    </div>
  </template>