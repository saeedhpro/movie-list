<template>
  <div class="flex mx-auto mt-4 items-center space-x-1">
    <a @click="paginatePrev" href="#" class="flex items-center px-4 py-2 text-gray-500 bg-gray-300 rounded-md">
      &lt;
    </a>
    <span class="px-4 py-2 rounded-md bg-blue-400 text-white hover:bg-blue-400 hover:text-white">
          {{ page }}
        </span>
    <a @click="paginateNext" href="#" class="px-4 py-2 font-bold text-gray-500 bg-gray-300 rounded-md hover:bg-blue-400 hover:text-white">
      &gt;
    </a>
  </div>
</template>

<script setup>
const emits = defineEmits(['paginate'])

const props = defineProps({
  page: {
    type: Number,
    default: 1
  },
  lastPage: {
    type: Number,
    default: 1
  },
})
const paginateNext = (e) => {
  e.preventDefault()
  if (props.lastPage == props.page) return
  emits('paginate', (props.page + 1))
}

const paginatePrev = (e) => {
  e.preventDefault()
  if (props.page == 1) return
  emits('paginate', (props.page - 1))
}
</script>

<style scoped>

</style>