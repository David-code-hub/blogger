<template>
  <div class="w-full grid grid-cols-6 mx-auto gap-12 sm:px-0 px-10 sm:pr-24">
    <div
      class="sm:block hidden transition-all duration-300 bg-gray-50 transform h-full border-r-0 pl-24 pr-12 border-slate-100 pt-12 h-screen sticky top-0"
      :class="[!showSide ? '-translate-x-full' : 'sm:col-span-2']"
    >
      <!--additional blog content eg filter,search,categories-->
      <HomeSidebar v-if="showSide" />
      <!-- <button
        @click="showSide = !showSide"
        class="absolute border top-3 p-2 rounded-xl bg-white duration-300 hover:bg-gray-100 flex items-center"
        :class="[showSide ? '-right-5' : '-right-12']"
      >
        <Icon name="uil:arrow-left" class="text-2xl text-black" />
      </button> -->
    </div>

    <div
      class="pb-12"
      :class="[showSide ? 'col-span-6 sm:col-span-4' : 'col-span-5']"
    >
      <NavbarTop />
      <!--handle layouts-->
      <div
        class="grid gap-7 pt-12 align-center"
        :class="[showSide ? 'grid-cols-1 sm:grid-cols-2' : 'grid-cols-3']"
      >
        <!--search-->
        <div
          class="hidden sm:flex justify-between mb-7"
          :class="[showSide ? 'sm:col-span-2' : 'col-span-3']"
        >
          <h1 class="font-regular mt-3 text-lg mb-0 leading-none">
            Recent Blog Posts
          </h1>
          <input
            placeholder="Search blogs..."
            v-model="search"
            class="border py-2 px-3 focus:border-blue-900 rounded-xl min-w-[250px] outline-none"
          />
        </div>
        <!--end search
          handleSearch()"
          :key="blog.title"
          :author="blog.author"
          :title="blog.title"
          :blog-image="blog.blogImage"
          :description="blog.description"
        />
        -->

        <div v-if="loadingAnime" class="text-center w-full mx-auto col-span-2">
          <Icon
            name="svg-spinners:180-ring-with-bg"
            class="text-2xl text-black"
          />
          <p>loading...</p>
        </div>
        <BlogCard
          v-else
          v-for="a in anime"
          :key="a?.attributes?.slug"
          :author="{
            profileImage: a?.attributes?.posterImage?.tiny,
            name: a?.attributes?.canonicalTitle,
            title: a?.attributes?.averageRating,
          }"
          :title="a?.attributes?.canonicalTitle"
          :blog-image="
            a?.attributes?.coverImage?.original ||
            a?.attributes?.posterImage?.original
          "
          :description="a?.attributes?.synopsis.slice(0, 200) + '...'"
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
const anime = ref<any[]>();
const loadingAnime = ref(false);

function handleSearch() {
  return blogs.filter((item: any) =>
    item.title.toLowerCase().includes(search.value.toLowerCase())
  );
}

async function getAnime() {
  try {
    loadingAnime.value = true;
    const response = await fetch("https://kitsu.io/api/edge/anime");
    const data = await response.json();
    anime.value = data.data;
    // console.log(data.data);
  } catch (error) {
    console.error("Error while fetching anime", error);
  } finally {
    loadingAnime.value = false;
  }
}
getAnime();
</script>
