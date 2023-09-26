<template>
    <div class="p-8">
    <button class="text-white text-2xl font-semibold hover:underline cursor-pointer" type="button">
      Search for genre
    </button>
    <div class="py-1.5">
      <!-- spacer -->
    </div>
    <div class="grid xl:grid-cols-5 lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 gap-6">
      <CategorySelect category="Podcasts" image="https://picsum.photos/id/40/300/300" />
      <CategorySelect category="Pop" image="https://picsum.photos/id/41/300/300" />
      <CategorySelect category="AudioBooks" image="https://picsum.photos/id/42/300/300" />
      <CategorySelect category="Rock" image="https://picsum.photos/id/43/300/300" />
      <CategorySelect category="Podcasts" image="https://picsum.photos/id/44/300/300" />
    </div>
  </div>
</template>

<script setup>
import CategorySelect from "../components/CategorySelect.vue";
</script>

<style scoped>

</style>