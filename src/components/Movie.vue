<template>
  <div class="w-full flex flex-row align-middle justify-start border-indigo-100 bg-slate-100 rounded-3xl py-2 px-4 mb-2 text-white">
    <div class="w-1/2 flex flex-col align-middle justify-start ">
      <div class="w-full">Name: {{ movie?.title }} ({{ movie?.imdb_rating }})</div>
      <div class="w-full">Country: {{ movie?.country }} ({{ movie?.year }})</div>
      <div class="w-full flex flex-row flex-wrap align-middle justify-start items-start">
        Genres: <div class="ml-1 mr-2" v-for="(g, i) in movie?.genres" :key="i">{{ g }},</div>
      </div>
      <div class="w-full flex flex-row flex-wrap align-middle justify-start items-start">
        Images:
        <div class="ml-1 mr-2" v-for="(image, i) in movie?.images" :key="i">
          <img class="w-[75px]" :src="image" :alt="movie?.title">
        </div>
      </div>

    </div>
    <div class="w-1/2">
      <img class="w-[200px]" :src="movie.poster" :alt="movie?.title">
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  movie: {
    type: Object,
    default: null
  }
})
</script>

<style scoped>

</style>