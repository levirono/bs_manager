<template>
    <div class="min-h-screen bg-gray-100">
      <UContainer>
        <UNavbar>
          <template #left>
            <ULink to="/" class="font-bold text-2xl">
              Business App
            </ULink>
          </template>
          <template #right>
            <UButtonGroup>
              <UButton to="/" label="Home" color="gray" variant="ghost" />
              <UButton to="/admin" label="Admin" color="gray" variant="ghost" />
              <UButton to="/sales" label="Sales" color="gray" variant="ghost" />
            </UButtonGroup>
          </template>
        </UNavbar>
        <main class="py-8">
          <slot />  <!-- This is where the page content will be rendered -->
        </main>
      </UContainer>
    </div>
  </template>