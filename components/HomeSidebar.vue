<template>
  <div>
    <div class="mb-7">
      <h1 class="text-2xl font-bold mb-1">Categories</h1>
      <p class="text-gray-400 text-base">Filter By Categories</p>
    </div>
    <div
      v-for="category in categories"
      :key="category.id"
      @click="selectedCategory = category.name"
      class="font-regular text-base mb-4 w-max py-1 px-2 rounded-xl cursor-pointer duration-200"
      :class="[
        selectedCategory === category.name
          ? 'bg-green-900 text-white'
          : 'bg-green-100 text-green-900',
      ]"
    >
      {{ category.name }}
    </div>
  </div>
</template>

<script setup lang="ts">
const selectedCategory = ref("");
</script>

<style scoped></style>
