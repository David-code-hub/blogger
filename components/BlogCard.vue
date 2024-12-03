<template>
  <div class="cursor-pointer group/blogcard mb-2">
    <!--handle image-->
    <div class="rounded-xl object-cover h-[250px] w-full mb-3 overflow-hidden">
      <img
        :src="props.blogImage"
        alt="blog image"
        class="object-cover h-[250px] w-full group-hover/blogcard:scale-125 duration-300 transition ease-in-out"
      />
    </div>
    <!--handle blog content-->
    <div>
      <h1
        class="text-2xl font-bold text-black mb-2 group-hover/blogcard:text-green-900 truncate"
      >
        {{ props.title }}
      </h1>
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
          <p class="font-semibold mb-0">
            {{ props.author?.name }}
          </p>
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
