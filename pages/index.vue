<template>
  <div class="w-full grid grid-cols-5 pr-24 mx-auto gap-12">
    <div
      class="transition-all duration-300 transform h-full border-r pl-24 border-slate-100 pt-12 h-screen sticky top-0"
      :class="[!showSide ? '-translate-x-full' : 'col-span-2']"
    >
      <!--additional blog content eg filter,search,categories-->
      <HomeSidebar v-if="showSide" />
      <button
        @click="showSide = !showSide"
        class="absolute border top-3 p-2 rounded-xl bg-white duration-300 hover:bg-gray-100 flex items-center"
        :class="[showSide ? '-right-5' : '-right-12']"
      >
        <Icon name="uil:arrow-left" class="text-2xl text-black" />
      </button>
    </div>

    <div class="pb-12" :class="[showSide ? 'col-span-3' : 'col-span-4']">
      <!--handle layouts-->
      <div
        class="grid gap-7 pt-12"
        :class="[showSide ? 'grid-cols-2' : 'grid-cols-3']"
      >
        <div
          class="flex justify-between mb-7"
          :class="[showSide ? 'col-span-2' : 'col-span-3']"
        >
          <h1 class="font-bold text-2xl mb-0">Recent Blog Posts</h1>
          <input
            placeholder="Search blogs..."
            v-model="search"
            class="border py-2 px-3 focus:border-blue-900 rounded-xl min-w-[250px] outline-none"
          />
        </div>
        <BlogCard
          v-for="blog in handleSearch()"
          :key="blog.title"
          :author="blog.author"
          :title="blog.title"
          :blog-image="blog.blogImage"
          :description="blog.description"
        />
        <div class="col-span-2" v-if="!handleSearch().length">
          <h1 class="font-semibold">No blog posts... 👀</h1>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
import { blogs } from "../composables/data";

const search = ref("");
const showSide = ref(true);

function handleSearch() {
  return blogs.filter((item: any) =>
    item.title.toLowerCase().includes(search.value.toLowerCase())
  );
}
</script>
