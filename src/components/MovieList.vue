<template>
  <div class="flex flex-col">
    <div class="flex flex-row flex-wrap justify-start items-start">
      <Movie :movie="movie" v-for="(movie, i) in movies" :key="i"/>
    </div>
    <div class="flex flex-row">
      <Pagination :page="page" :last-page="lastPage" @paginate="paginate"/>
    </div>
  </div>
</template>

<script setup>
import Movie from "@/components/Movie.vue";
import Pagination from "@/components/Pagination.vue";

const emits = defineEmits(['paginate'])
const props = defineProps({
  movies: {
    type: Array,
    default: []
  },
  page: {
    type: Number,
    default: 1
  },
  lastPage: {
    type: Number,
    default: 1
  }
})

const paginate = (page) => {
  emits('paginate', page)
}
</script>

<style scoped>

</style>