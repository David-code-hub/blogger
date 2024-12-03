<template>
  <div class="w-full grid grid-cols-5 pr-24 mx-auto gap-12">
    <div
      class="col-span-2 h-full border-r pl-24 border-slate-100 pt-20 bg-gray-50 h-screen sticky top-0"
    >
      <!--additional blog content eg filter,search,categories-->
      <HomeSidebar />
    </div>
    <div class="col-span-3">
      <!--handle layouts-->
      <!--hide top section for now-->
      <!-- <div>
        <div class="grid grid-cols-2 gap-7 pt-20">
          <h1 class="col-span-2 font-bold text-2xl mb-0">Recent Blog Posts</h1>
          <BlogCard
            v-for="blog in blogs.slice(0, 2)"
            :key="blog.title"
            :author="blog.author"
            :title="blog.title"
            :blog-image="blog.blogImage"
            :description="blog.description"
          />
        </div>
      </div> -->

      <div class="grid grid-cols-2 gap-7 pt-20">
        <div class="col-span-2 flex justify-between">
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

function handleSearch() {
  return blogs.filter((item: any) =>
    item.title.toLowerCase().includes(search.value.toLowerCase())
  );
}
</script>
