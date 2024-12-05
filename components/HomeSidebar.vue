<template>
  <div>
    <div class="mb-4">
      <div class="flex items-center gap-2 mb-3">
        <img
          :src="personalDetails.profileImage"
          class="h-[50px] w-[50px] rounded-full object-cover"
          alt="profile image"
        />
        <div>
          <p class="text-lg font-semibold text-black">
            {{ personalDetails.name }}
          </p>
          <p class="text-sm font-normal text-gray-400">
            {{ personalDetails.subtitle }}
          </p>
        </div>
      </div>
      <p class="text-sm text-gray-400 font-normal">
        {{ personalDetails.bio }}
      </p>
    </div>
    <div class="mb-4">
      <h1 class="text-sm mb-3">Let's Connect</h1>
      <div class="flex gap-1">
        <a
          href="https://github.com/David-code-hub/blogger"
          target="_blank"
          class="p-2 rounded-full duration-300 hover:bg-gray-100 flex items-center"
        >
          <Icon name="uil:github" class="text-2xl text-black" />
        </a>
        <a
          href="https://www.linkedin.com/in/david-felix-467505128/"
          target="_blank"
          class="p-2 rounded-full duration-300 hover:bg-gray-100 flex items-center"
        >
          <Icon name="uil:linkedin" class="text-2xl text-black" />
        </a>

        <a
          href="https://magenta-malasada-96024c.netlify.app/"
          target="_blank"
          class="p-2 rounded-full duration-300 hover:bg-gray-100 flex items-center"
        >
          <Icon name="uil:link" class="text-2xl text-black" />
        </a>
      </div>
    </div>
    <div class="mb-4">
      <h1 class="text-1xl font-semibold">Categories</h1>
    </div>
    <div class="flex flex-col">
      <div
        v-for="category in categories"
        :key="category.id"
        @click="selectedCategory = category.name"
      >
        <div
          class="font-regular m-1 text-sm mb-4 w-max py-1 px-2 rounded-xl cursor-pointer duration-200"
          :class="[
            selectedCategory === category.name
              ? 'bg-gray-900 text-white'
              : 'bg-gray-100 text-gray-900',
          ]"
        >
          {{ category.name }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const selectedCategory = ref("");
</script>

<style scoped></style>
