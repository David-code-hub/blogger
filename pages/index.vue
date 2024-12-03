<template>
  <div class="w-full grid grid-cols-3 px-24 mx-auto gap-12 my-7">
    <div class="col-span-1 h-full rounded-xl">
      <!--additional blog content eg filter,search,categories-->
      <HomeSidebar />
    </div>
    <div class="col-span-2">
      <!--handle layouts-->
      <!--top section-->
      <div>
        <div class="grid grid-cols-2 gap-7">
          <h1 class="col-span-2 font-bold text-2xl mb-0">Recent Blog Posts</h1>
          <BlogCard
            v-for="blog in blogs.slice(0, 2)"
            :key="blog.title"
            :author="blog.author"
            :title="blog.title"
            :blog-image="blog.blogImage"
            :description="blog.description"
          />
          <!-- <div class="grid grid-row-2 grid-cols-1">
            <BlogCard :show-image-on-side="true" />
            <BlogCard :show-image-on-side="true" />
          </div> -->
        </div>
      </div>

      <div class="grid grid-cols-2 gap-7 mt-12">
        <div class="col-span-2 flex justify-between">
          <h1 class="font-bold text-2xl mb-0">Popular Blog Posts</h1>
          <input
            placeholder="Search..."
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
  return blogs
    .slice(2, 5)
    .filter((item: any) =>
      item.title.toLowerCase().includes(search.value.toLowerCase())
    );
}
</script>
