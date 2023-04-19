<template>
  <div class="container h-screen mx-auto">
    <div>
      <h1 class="mb-5 text-3xl font-bold text-center">Dashboard</h1>
    </div>
    <div class="grid grid-cols-6 gap-2 h-4/5">
      <div class="col-span-1 p-5 mb-4 text-2xl bg-purple-300">
        <h2 class="mb-4 font-bold">Chapters</h2>
        <div
          v-for="chapter in chapters"
          :key="chapter.slug"
          class="flex flex-col mb-4 space-y-4"
        >
          <h4>
            {{ chapter.title }}
          </h4>
          <NuxtLink
            v-for="(lesson, index) in chapter.lessons"
            :key="lesson.slug"
            class="inline-block px-4 py-2 text-sm text-gray-600 uppercase"
            :to="`/course/chapter/${chapter.slug}/lesson/${lesson.slug}`"
          >
            <span> {{ index + 1 }}. </span>
            <span>{{ lesson.title }}</span>
          </NuxtLink>
        </div>
      </div>
      <div class="col-span-5 p-5 bg-yellow-200">
        <NuxtPage />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const { chapters } = useCourse();
</script>
