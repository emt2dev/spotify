<template>
  <div class="p-8">
    <button class="text-white text-2xl font-semibold hover:underline cursor-pointer" type="button">
      Podcasts to make you smarter
    </button>
    <div class="py-1.5">
      <!-- spacer -->
    </div>
    <div class="flex items-center">
      <HomeCard image="https://picsum.photos/id/30/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard image="https://picsum.photos/id/45/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="md:block hidden" image="https://picsum.photos/id/65/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="lg:block hidden" image="https://picsum.photos/id/67/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="xl:block hidden" image="https://picsum.photos/id/100/300/300" title="Title is here" subTitle="Subtitle goes here" />
    </div>
  </div>
  <div class="p-8">
    <button class="text-white text-2xl font-semibold hover:underline cursor-pointer" type="button">
      Recommended Radio
    </button>
    <div class="py-1 5">
      <!-- spacer -->
    </div>
    <div class="flex items-center">
      <HomeCard image="https://picsum.photos/id/30/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard image="https://picsum.photos/id/45/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="md:block hidden" image="https://picsum.photos/id/65/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="lg:block hidden" image="https://picsum.photos/id/67/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="xl:block hidden" image="https://picsum.photos/id/100/300/300" title="Title is here" subTitle="Subtitle goes here" />
    </div>
  </div>
  <div class="p-8">
    <button class="text-white text-2xl font-semibold hover:underline cursor-pointer" type="button">
      Recommended Songs
    </button>
    <div class="py-1 5">
      <!-- spacer -->
    </div>
    <div class="flex items-center">
      <HomeCard image="https://picsum.photos/id/30/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard image="https://picsum.photos/id/45/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="md:block hidden" image="https://picsum.photos/id/65/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="lg:block hidden" image="https://picsum.photos/id/67/300/300" title="Title is here" subTitle="Subtitle goes here" />
      <HomeCard class="xl:block hidden" image="https://picsum.photos/id/100/300/300" title="Title is here" subTitle="Subtitle goes here" />
    </div>
  </div>
</template>

<script setup>
import HomeCard from '../components/HomeCard.vue';


</script>

<style scoped>

</style>