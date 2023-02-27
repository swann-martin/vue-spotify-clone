<script setup>
import Play from 'vue-material-design-icons/Play.vue';
import Pause from 'vue-material-design-icons/Pause.vue';
import Heart from 'vue-material-design-icons/Heart.vue';
import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue';
import ClockTimeThreeOutline from 'vue-material-design-icons/ClockTimeThreeOutline.vue';
import artist from '../artist.json';
import SongRow from '../components/SongRow.vue';

import { useSongStore } from '../stores/song';
import { storeToRefs } from 'pinia';
const useSong = useSongStore();
const { isPlaying, currentTrack, currentArtist } = storeToRefs(useSong);

const playFunc = () => {
  if (currentTrack.value) {
    useSong.playOrPauseThisSong(currentArtist.value, currentTrack.value);
    return;
  }

  useSong.playFromFirst();
};
</script>

<template>
  <div class="p-8">
    <button
      type="button"
      class="text-2xl font-semibold text-white cursor-pointer hover:underline"
    >
      {{ artist.name }}
    </button>

    <div class="py-1.5">
      <div class="flex relative items-center w-full h-full">
        <img :src="artist.albumCover" alt="artist album cover" width="140" />

        <div class="ml-5 w-full">
          <div
            style="font-size: 33px"
            class="absolute top-0 w-full font-semibold text-white cursor-pointer hover:underline"
          >
            {{ artist.name }}
          </div>
          <div class="text-gray-300 text-[13px] flex">
            <div class="flex">Album</div>
            <div class="flex ml-2">
              <div class="mt-2 mr-2 circle" />
              <span class="-ml-05">{{ artist.releaseYear }}</span>
            </div>
            <div class="flex ml-2">
              <div class="mt-2 mr-2 circle" />
              <span class="-ml-05">{{ artist.tracks.length }} songs</span>
            </div>
          </div>

          <div
            class="flex absolute bottom-0 gap-4 justify-start items-center mb-1.5"
          >
            <button
              type="button"
              @click="playFunc"
              class="p-1 bg-white rounded-full"
            >
              <Play v-if="!isPlaying" fillColor="#181818" :size="25" />
              <Play v-else fillColor="#181818" :size="25" />
            </button>

            <button type="button" class="">
              <Heart fillColor="#1BD760" :size="30" />
            </button>
            <button type="button" class="">
              <DotsHorizontal fillColor="#FFF" :size="25" />
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="mt-6"></div>
    <div class="flex justify-between items-center px-5 pt-2">
      <div class="flex justify-between items-center text-gray-400">
        <div class="mr-7">#</div>
        <div class="text-sm">Title</div>
      </div>
      <div>
        <ClockTimeThreeOutline fillColor="#FFF" :size="18" />
      </div>
    </div>
    <div class="border-b border-b-[#2A2A2A] mt-2 mb-4"></div>
    <ul
      class="w-full text-white"
      v-for="(track, index) in artist.tracks"
      :key="track"
    >
      <SongRow :artist="artist" :track="track" :index="++index" />
    </ul>
  </div>
</template>

<style scoped>
.circle {
  width: 4px;
  height: 4px;
  background-color: rgb(189, 189, 189);
  border-radius: 50%;
}
</style>
