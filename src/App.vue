<template>
  <div>
    <div class="w-[calc(100%-240px)] h-[60px] fixed right-0 z-20 bg-[#101010] bg-opacity-80 flex items-center justify-between">
      <div class="flex items-center ml-6">
        <button type="button" class="rounded-full bg-black p-[1px] cursor-pointer">
          <ChevronLeft fillColor="#FFFFFF" :size="30" />
        </button>
        <button type="button" class="rounded-full bg-black p-[1px] cursor-pointer ml-4">
          <ChevronRight fillColor="#FFFFFF" :size="30" />
        </button>
      </div>
        <button
            @click="openMenu=!openMenu" :class="openMenu ? 'bg-[#282828]' : 'bg-[#101010]'"
          class="bg-black hover:bg-[#282828] rounded-full p-0.5 mr-8 mt-0.5 cursor-pointer">
          <div class="flex items-center">
            <img src="/src/assets/profile.png" alt="" class="rounded-full" width="27" />
            
            <div class="text-white text-[14px] ml-1.5 font-semibold">
              David Duron
            </div>

              <ChevronDown v-if="!openMenu" @click="openMenu=true" fillColor="#FFFFFF" :size="25" />
              <ChevronUp v-else @click="openMenu=false" fillColor="#FFFFFF" :size="25" />

          </div>
        </button>

        <span
          v-if="openMenu"
          class="fixed w-[190px] bg-[#282828] shadow-2xl z-50 rounded-sm top-[52px] right-[35px] p-1 cursor-pointer">
          <ul class="text-gray-200 font-semibold text-[14px]">
            <li class="px-3 py-2.5 hover:bg-[#3E3D3D] border-b border-b-gray-600">
              Profile
            </li>
            <li class="px-3 py-2.5 hover:bg-[#3E3D3D]">
              Log Out
            </li>
          </ul>
        </span>
    </div>

    <div
      id="SideNav"
      class="h-[100%] p-6 w-[240px] fixed z-50 bg-black">
        <RouterLink to="/">
          <img src="/images/icons/spotify-logo.png" width="125" alt="">
        </RouterLink>
        <div class="my-8">
          <ul>
            <RouterLink to="/">
              <MenuItem class="ml-[1px]" :iconSize="23" name="Home" iconString="home" pageUrl="/"  />
            </RouterLink>
            <RouterLink to="/search">
              <MenuItem class="ml-[1px]" :iconSize="24" name="Search" iconString="search" pageUrl="/search"  />
            </RouterLink>
            <RouterLink to="/library">
              <MenuItem class="ml-[2px]" :iconSize="23" name="Library" iconString="library" pageUrl="/"  />
            </RouterLink>
            <div class="py-3 5">
              <!-- spacing -->
            </div>
            <MenuItem :iconSize="24" name="Create Playlist" iconString="playlist" pageUrl="/playlist" />
            <MenuItem  :iconSize="27" name="Liked Songs" iconString="liked" pageUrl="/liked" />
          </ul>
          <div class="border-b border-b-gray-700">
            <!-- border -->
          </div>
          <ul>
            <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">
              My Playlist #1
            </li>
            <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">
              My Playlist #2
            </li>
            <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">
              My Playlist #3
            </li>
            <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">
              My Playlist #4
            </li>
          </ul>
        </div>
    </div>
    <div class="fixed right-0 top-0 w-[calc(100%-240px)] overflow-auto h-full bg-gradient-to-b from-[#1c1c1c] to-[#101010]">
      <div class="mt-[70px]">
        <!-- spacer -->
      </div>
      <RouterView />
      <div class="mb-[100px]">
        <!-- spacer -->
      </div>
    </div>
  </div>

  <MusicPlayer />
</template>

<script setup>
// import HomeView from './views/HomeView.vue';

// libraries
import { ref, onMounted } from 'vue';
import { RouterLink, RouterView } from 'vue-router';

// components
import MenuItem from '/src/components/MenuItem.vue';
import MusicPlayer from '/src/components/MusicPlayer.vue';

// vue material
import ChevronUp from 'vue-material-design-icons/ChevronUp.vue';
import ChevronDown from 'vue-material-design-icons/ChevronDown.vue';
import ChevronRight from 'vue-material-design-icons/ChevronRight.vue';
import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue';

import { useSongStore } from './stores/song';
import { storeToRefs } from 'pinia';

const useSong = useSongStore;
const { isPlaying, currentTrack } = storeToRefs(useSong);

onMounted(() => {
  // ensure the isplaying bool is false
  isPlaying.value = false;
});

let openMenu = ref(false);
</script>

<style scoped>

</style>