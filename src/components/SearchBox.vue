<template>
  <div class="w-full bg-white rounded-full py-2 px-4 flex items-center relative">
    <input @input="onTextWrite" type="text" class="flex-1 px-4 py-2 rounded-full border border-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Search">
    <div class="absolute right-6">
      <svg xmlns="http://www.w3.org/2000/svg" class="cursor-pointer h-5 w-5 text-blue-500" viewBox="0 0 20 20" fill="currentColor">
        <path fill-rule="evenodd" d="M12.707 11.293a1 1 0 010 1.414l-2.829 2.828a1 1 0 01-1.414-1.414l2.828-2.828a1 1 0 011.414 0zM9.5 15a5.5 5.5 0 100-11 5.5 5.5 0 000 11z" clip-rule="evenodd" />
      </svg>
    </div>
  </div>
</template>

<script setup>
const emits = defineEmits(['search'])
const onTextWrite = (e) => {
  const q = e.target?.value ?? ''
  emits('search', q)
}

</script>

<style scoped>

</style>