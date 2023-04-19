<template>
  <div>
    <p class="mb-4 text-sm font-bold text-gray-500 uppercase">
      Lesson {{ chapter.number }} - {{ lesson.number }}
    </p>
    <h2 class="mb-5 text-3xl font-bold">{{ lesson.title }}</h2>
  </div>
  <div class="flex mb-4">
    <a
      class="inline-block px-4 py-2 text-sm font-bold text-white uppercase bg-purple-500 rounded hover:bg-purple-600"
      v-if="lesson.downloadURL"
      :href-="lesson.downloadURL"
      >Download source code</a
    >
  </div>
  <div class="mb-4">
    <VideoPlayer v-if="lesson.videoId" :videoId="lesson.downloadURL" />
  </div>
  <div>
    <p>
      {{ lesson.text }}
    </p>
  </div>
  <!-- <div>
    <p>Chapter slug: {{ $route.params.chapterSlug }}</p>
    <p>Lesson slug: {{ $route.params.lessonSlug }}</p>
    <p>Chapter title: {{ chapter.title }}</p>
    <p>Lesson title: {{ lesson.title }}</p>
  </div> -->
</template>

<script setup>
import VideoPlayer from "~~/components/VideoPlayer.vue";
const route = useRoute();
const course = useCourse();

const chapter = computed(() => {
  return course.chapters.find(
    (chapter) => chapter.slug === route.params.chapterSlug
  );
});

const lesson = computed(() => {
  return chapter.value.lessons.find(
    (lesson) => lesson.slug === route.params.lessonSlug
  );
});
</script>
