<template>
  <div class="w-full grid grid-cols-3 container mx-auto gap-7 my-7">
    <div class="col-span-1 h-full bg-gray-50">
      <!--additional blog content eg filter,search,categories-->
    </div>
    <div class="col-span-2">
      <!--handle layouts-->
      <!--top section-->
      <div>
        <div class="grid grid-cols-2 gap-7">
          <BlogCard />
          <div class="grid grid-row-2 grid-cols-1">
            <BlogCard />
            <BlogCard />
          </div>
        </div>
      </div>
      <div class="grid grid-cols-3 gap-7 mt-12">
        <BlogCard v-for="_ in 3" :key="_" />
      </div>
    </div>
  </div>
</template>
