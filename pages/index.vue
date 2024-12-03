<template>
  <div class="w-full grid grid-cols-3 px-24 mx-auto gap-12 my-7">
    <div class="col-span-1 h-full bg-gray-200 rounded-xl">
      <!--additional blog content eg filter,search,categories-->
    </div>
    <div class="col-span-2">
      <!--handle layouts-->
      <!--top section-->
      <div>
        <div class="grid grid-cols-2 gap-7">
          <h1 class="col-span-2 font-bold text-2xl mb-0">Recent Blog Posts</h1>
          <BlogCard
            v-for="blog in blogDummyData.slice(0, 2)"
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
        <h1 class="col-span-2 font-bold text-2xl mb-0">Popular Blog Posts</h1>
        <BlogCard
          v-for="blog in blogDummyData.slice(2, 5)"
          :key="blog.title"
          :author="blog.author"
          :title="blog.title"
          :blog-image="blog.blogImage"
          :description="blog.description"
        />
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
const blogDummyData = [
  {
    title: "Getting Started with Vue.js",
    description:
      "A beginner's guide to understanding the basics of Vue.js and setting up your first Vue app.",
    blogImage:
      "https://images.unsplash.com/photo-1652946998511-41f80a8096ff?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    author: {
      name: "John Doe",
      profileImage: "https://i.pravatar.cc/150?img=3",
      title: "Front-End Developer",
    },
  },
  {
    title: "Vue.js vs React: A Comparison",
    description:
      "In this post, we compare Vue.js with React, looking at their similarities, differences, and when to choose each.",
    blogImage:
      "https://images.unsplash.com/photo-1547219469-75c19c0bd220?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    author: {
      name: "Jane Smith",
      profileImage: "https://i.pravatar.cc/150?img=5",
      title: "Full Stack Developer",
    },
  },
  {
    title: "Vue CLI: A Powerful Tool for Developers",
    description:
      "Explore Vue CLI, a powerful tool that simplifies project setup, development, and builds with Vue.js.",
    blogImage:
      "https://images.unsplash.com/photo-1495584816685-4bdbf1b5057e?q=80&w=1548&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    author: {
      name: "Alice Green",
      profileImage: "https://i.pravatar.cc/150?img=8",
      title: "JavaScript Engineer",
    },
  },
  {
    title: "Understanding Vuex for State Management",
    description:
      "A detailed explanation of Vuex, Vue.js' state management library, and how to use it effectively in your app.",
    blogImage:
      "https://plus.unsplash.com/premium_photo-1675819564298-f393097e19a6?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    author: {
      name: "Bob Williams",
      profileImage: "https://i.pravatar.cc/150?img=2",
      title: "Software Engineer",
    },
  },
  {
    title: "How to Build Reusable Components in Vue.js",
    description:
      "Learn how to build reusable and scalable components in Vue.js, and why component-based architecture is key to modern web development.",
    blogImage:
      "https://images.unsplash.com/photo-1529419412599-7bb870e11810?q=80&w=1587&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
    author: {
      name: "Charlie Brown",
      profileImage: "https://i.pravatar.cc/150?img=7",
      title: "Frontend Architect",
    },
  },
];
</script>
