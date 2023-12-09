
<template>
  <main class="w-full">
    <div class="flex flex-col align-middle justify-start p-4">
      <SearchBox @search="search" />
      <MovieList :last-page="lastPage" :page="page" :movies="movies" @paginate="paginate"/>
    </div>
  </main>
</template>
<script setup>
import SearchBox from "@/components/SearchBox.vue";
import {ref} from "vue";
import { useFetch } from '@vueuse/core'
import MovieList from "@/components/MovieList.vue";

const name = ref('')
const page = ref(1)
const lastPage = ref(1)
const movies = ref([])

const doSearch = async() => {
  movies.value = []
  const { isFetching, error, data: moviesData } = await useFetch(`https://moviesapi.ir/api/v1/movies?q=${name.value}&page=${page.value}`).json()
  movies.value = moviesData.value.data
  lastPage.value = moviesData.value.metadata.page_count
}
const search = (q) => {
  name.value = q
  doSearch()
}

const paginate = (p) => {
  page.value = p
  doSearch()
}

doSearch()
</script>

<style scoped>
</style>