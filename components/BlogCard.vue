<template>
  <div>
    <!--handle image-->
    <img
      src="https://images.unsplash.com/photo-1547219469-75c19c0bd220?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
      alt="blog image"
      class="rounded-xl object-cover max-h-[250px] w-full"
    />
    <!--handle blog content-->
    <h1 class="text-2xl font-bold text-black mb-2 mt-3">
      How emit works in Vue
    </h1>
    <p class="text-sm text-gray-400">
      Lorem ipsum dolor disficis en amet. Una mesa para dos personas dolor
      disficis en amet. Lorem ipsum dolor disficis en amet. Una mesa para dos
      personas dolor disficis en...
    </p>
    <!--handle author details-->
    <div class="flex gap-2 items-center mt-3">
      <img
        src="https://images.unsplash.com/photo-1522075469751-3a6694fb2f61?q=80&w=1480&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
        class="rounded-full w-[50px] h-[50px] object-cover"
        alt="author avatar"
      />
      <div>
        <p class="font-semibold mb-0">John Doe</p>
        <p class="text-sm text-gray-400">Frontend Developer</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped></style>
