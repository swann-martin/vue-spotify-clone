<script setup>
import { ref, watch, onMounted } from 'vue';
import Heart from 'vue-material-design-icons/Heart.vue';
import Play from 'vue-material-design-icons/Play.vue';
import Pause from 'vue-material-design-icons/Pause.vue';
import SkipBackward from 'vue-material-design-icons/SkipBackward.vue';
import SkipForward from 'vue-material-design-icons/SkipForward.vue';
import PictureInPictureBottomRight from 'vue-material-design-icons/PictureInPictureBottomRight.vue';

import { useSongStore } from '../stores/song';
import { storeToRefs } from 'pinia';
const useSong = useSongStore();
const { isPlaying, audio, currentTrack, currentArtist } = storeToRefs(useSong);

let isHover = ref(false);
let isTrackTimeCurrent = ref(null);
let isTrackTimeTotal = ref(null);
let seeker = ref(null);
let seekTime = ref(0);
let seekContainer = ref(null);
let range = ref(0);

onMounted(() => {
  setTimeout(() => {
    timeupdate();
    loadedmetadata();
  }, 300);

  if (currentTrack.value) {
    seeker.value.addEventListener('change', () => {
      const time = audio.value.duration * (seeker.value.value / 100);
      audio.value.currentTime = time;
    });
    seeker.value.addEventListener('mousedown', () => {
      audio.value.pause();
      isPlaying.value = false;
    });
    seeker.value.addEventListener('mouseup', () => {
      audio.value.play();
      isPlaying.value = true;
    });

    seekContainer.value.addEventListener('click', () => {
      const clickPosition =
        (e.pageX - seekContainer.value.offsetLeft) /
        seekContainer.value.offsetWidth;
      audio.value.currentTime = clickPosition * audio.value.duration;
      seeker.value.value =
        (100 / audio.value.duration) * audio.value.currentTime;
    });
  }
});

const timeupdate = () => {
  audio.value.addEventListener('timeupdate', () => {
    var minutes = Math.floor(audio.value.currentTime / 60);
    var seconds = Math.floor(audio.value.currentTime - minutes * 60);
    isTrackTimeCurrent.value =
      minutes + ':' + seconds.toString().padStart(2, '0');

    const value = (100 / audio.value.duration) * audio.value.currentTime;
    range.value = value;
    seeker.value = value;
  });
};

const loadedmetadata = () => {
  audio.value.addEventListener('loadedmetadata', () => {
    const duration = audio.value.duration;
    const minutes = Math.floor(duration / 60);
    const seconds = Math.floor(duration % 60);
    isTrackTimeTotal.value =
      minutes + ':' + seconds.toString().padStart(2, '0');
  });
};

watch(
  () => audio.value,
  () => {
    timeupdate();
    loadedmetadata();
  },
);

watch(
  () => isTrackTimeCurrent.value,
  (time) => {
    if (time && time === isTrackTimeTotal.value) {
      useSong.nextSong(currentTrack.value);
    }
  },
);
</script>

<template>
  <div
    id="MusicPlayer"
    class="w-full fixed flex items-center justify-between bottom-0 z-50 h-[90px] bg-[#181818] border-t border-t-[#272727]"
  >
    <div class="flex items-center w-1/4">
      <div class="flex items-center ml-4">
        <img
          class="rounded-sm shadow-2xl"
          width="55"
          :src="currentArtist.albumCover"
          alt="artist album cover"
        />
        <div class="ml-4">
          <div class="text-[14px] text-white hover:underline cursor-pointer">
            {{ currentTrack.name }}
          </div>
          <div
            class="text-[14px] text-gray-400 hover:underline hover:text-white cursor-pointer"
          >
            {{ currentArtist.name }}
          </div>
        </div>
      </div>
      <div class="flex items-center ml-8">
        <Heart fillColor="#1BD760" :size="20" />
        <PictureInPictureBottomRight class="ml-4" fillColor="#FFF" :size="18" />
      </div>
    </div>

    <section class="max-w[35%] mx-auto w-2/4 mb-3">
      <div class="flex-col justify-center items-center">
        <div class="flex items-center justify-center h-[30px]">
          <button class="mx-2">
            <SkipBackward
              fillColor="#FFF"
              :size="25"
              @click="useSong.prevSong(currentTrack)"
            />
          </button>
          <button class="p-1 bg-white rounded-full">
            <Pause
              v-if="isPlaying"
              fillColor="#181818"
              :size="25"
              @click="
                () => useSong.playOrPauseThisSong(currentArtist, currentTrack)
              "
            />
            <Play
              v-else
              fillColor="#181818"
              :size="25"
              @click="
                () => useSong.playOrPauseThisSong(currentArtist, currentTrack)
              "
            />
          </button>
          <button class="mx-2">
            <SkipForward
              fillColor="#FFF"
              :size="25"
              @click="() => useSong.nextSong(currentTrack)"
            />
          </button>
        </div>
      </div>

      <div class="flex items-center h-[25px]">
        <div
          v-if="isTrackTimeCurrent"
          class="text-white text-[12px] pr-2 pt-[11px]"
        >
          {{ isTrackTimeCurrent }}
        </div>
        <div
          ref="seekerContainer"
          class="relative mt-2 mb-3 w-full"
          @mouseenter="isHover = true"
          @mouseleave="isHover = false"
        >
          <input
            type="range"
            v-model="range"
            ref="seeker"
            class="absolute z-40 my-2 w-full h-0 bg-opacity-100 rounded-full appearance-none focus:outline-none accent-white"
            :class="{ rangeDotHidden: isHover }"
          />
          <div
            class="pointer-events-none mt-[6px] absolute h-[4px] z-10 inset-y-0 left-0 w-0"
            :style="`width : ${range}%;`"
            :class="isHover ? 'bg-green-500' : 'bg-white'"
          />

          <div
            class="absolute h-[4px] inset-y-0 left-0 w-full bg-gray-500 rounded-full mt-[6px]"
          />
        </div>

        <div
          v-if="isTrackTimeTotal"
          class="text-white text-[12px] pl-2 pt-[11px]"
        >
          {{ isTrackTimeTotal }}
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.rangeDotHidden[type='range']::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 15px;
  height: 15px;
  background: #1bd760;
  border-radius: 50%;
  cursor: pointer;
}
</style>
