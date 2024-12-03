<template>
  <div>
    <!--handle image-->
    <div
      class="rounded-xl object-cover h-[250px] w-full mb-3 overflow-hidden group/blogimage"
    >
      <img
        :src="props.blogImage"
        alt="blog image"
        class="object-cover h-[250px] w-full group-hover/blogimage:scale-125 duration-300 transition ease-in-out"
      />
    </div>
    <!--handle blog content-->
    <div>
      <h1 class="text-2xl font-bold text-black mb-2">{{ props.title }}</h1>
      <p class="text-sm text-gray-400">
        {{ props.description }}
      </p>
      <!--handle author details-->
      <div class="flex gap-2 items-center mt-4">
        <img
          :src="props.author?.profileImage"
          class="rounded-full w-[50px] h-[50px] object-cover"
          alt="author avatar"
        />
        <div>
          <p class="font-semibold mb-0">{{ props.author?.name }}</p>
          <p class="text-sm text-gray-400">{{ props.author?.title }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  title: String,
  description: String,
  blogImage: String,
  author: Object,
});
</script>

<style scoped></style>
