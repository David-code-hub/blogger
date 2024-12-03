<template>
  <div>
    <h1 class="text-2xl font-bold mb-7">Categories</h1>
    <div
      v-for="category in categories"
      :key="category.id"
      class="font-regular text-base mb-3"
    >
      {{ category.name }}
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped></style>
