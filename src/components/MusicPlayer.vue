<template>
    <div id="MusicPlayer"
        
        class="fixed flex items-center justify-between bottom-0 w-full z-50 h-[90px] bg-[#181818] border-t border-t-[#272727]"
        >
        test
    </div>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue';

import PictureInPictureBottomRight from 'vue-material-design-icons/PictureInPictureBottomRight.vue';
import Heart from 'vue-material-design-icons/Heart.vue';
import Play from 'vue-material-design-icons/Play.vue';
import Pause from 'vue-material-design-icons/Pause.vue';
import SkipBackward from 'vue-material-design-icons/SkipBackward.vue';
import SkipForward from 'vue-material-design-icons/SkipForward.vue';

import { useSongStore } from '../stores/song.js';
import { storeToRefs } from 'pinia';

const useSong = useSongStore;
const { isPlaying, audio, currentTrack,currentArtist } = storeToRefs(useSong);

let isHover = ref(false);
let isTrackTimeCurrent = ref(null);
let isTrackTimeTotal = ref(null);
let seeker = ref(null);
let seekerContainer = ref(null);
let range = ref(0);

onMounted(() => {
    if(audio.value) {
        setTimeout(() => {
            timeUpdate();
            loadMetaData();
        }, 300)
    }

    if(currentTrack.value) {
        seeker.value.addEventListener('change', function () {
            const time = audio.value.duration * (seeker.value.value / 100); // calculates time where seker bar is located.
            audio.value.currentTime = time;
        });

        seeker.value.addEventListener('mousedown', function () {
            audio.value.pause();
            isPlaying.value = false;
        });

        seeker.value.addEventListener('mouseup', function () {
            audio.value.play();
            isPlaying.value = true;
        });

        seekerContainer.value.addEventListener('click', function (event) {
            const clickPosition = (event.pageX - seekerContainer.value.offsetLeft) / seekerContainer.value.offsetWidth;
            const time = audio.value.duration * clickPosition;
            audio.value.currentTime = time;
            seeker.value.value = (100 / audio.value.duration) * audio.value.currentTime;
        });
    }
});

watch(() => audio.value, () => {
    timeUpdate();
    loadMetaData();
});

watch(() => isTrackTimeCurrent.value, (time) => {
    if(time && time === isTrackTimeTotal.value) {
        useSong.nextSong(currentTrack.value);
    }
})

const loadMetaData = () => {
    audio.value.addEventListener('loadmetadata', function() {
        const minutes = Math.floor(audio.duration / 60);
        const seconds = Math.floor(audio.duration % 60);
        isTrackTimeTotal.value = minutes + ":" + seconds.toString().padStart(2, '0');
    });
};

const timeUpdate = () => {
    audio.value.addEventListener('timeupdate', function() {
        var minutes = Math.floor(audio.value.currentTime / 60);
        var seconds = Math.floor(audio.value.currentTime - minutes * 60);
        isTrackTimeCurrent.value = minutes + ":" + seconds.toString().padStart(2, '0');
        const value = (100 / audio.value.duratoin) * audio.value.currentTime;
        range.value = value;
        seeker.value.value = value;
    });
};
</script>

<style scoped>

</style>