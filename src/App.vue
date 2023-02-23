<script setup>
import { ref, onMounted } from 'vue';
import { RouterLink, RouterView } from 'vue-router';
import MenuItem from './components/MenuItem.vue';
import ChevronUp from 'vue-material-design-icons/ChevronUp.vue';
import ChevronDown from 'vue-material-design-icons/ChevronDown.vue';
import ChevronRight from 'vue-material-design-icons/ChevronRight.vue';
import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue';

let openMenu = ref(false);
</script>

<template>
  <div>
    <div
      class="w-[calc(100%-240px)] h-[60px] fixed right-0 z-20 bg-[#101010] bg-opacity-80 flex items-center justify-between"
    >
      <div class="flex items-center ml-6">
        <button
          type="button"
          class="rounded-full bg-black hover:bg-[#282828] p-[1px] cursor-pointer"
        >
          <ChevronLeft fillColor="#FFF" :size="30" />
        </button>
        <button
          type="button"
          class="rounded-full bg-black hover:bg-[#282828] p-[1px] ml-4 cursor-pointer"
        >
          <ChevronRight fillColor="#FFF" :size="30" />
        </button>
      </div>
      <button
        @click="openMenu = !openMenu"
        :class="openMenu ? 'bg-[#282828]' : 'bg-black'"
        type="button"
        class="bg-black hover:bg-[#282828] p-0.5 mr-8 mt-0.5 cursor-pointer rounded-full"
      >
        <div class="flex items-center">
          <img
            class="rounded-full"
            width="27"
            src="https://media.licdn.com/dms/image/D5603AQFiS5wBCtvrbA/profile-displayphoto-shrink_100_100/0/1635497323034?e=1682553600&v=beta&t=v9_zeNvIBxDpt_A4uGEObPB3wsD6uwpQ3UXbBNSWl50"
            alt="picture"
          />
          <div class="text-white text-[14px] ml-1.5 font-semibold">
            Swann Martin
          </div>
          <ChevronDown
            fillColor="#FFF"
            :size="25"
            v-if="!openMenu"
            @click="openMenu = true"
          />
          <ChevronUp
            fillColor="#FFF"
            :size="25"
            v-if="openMenu"
            @click="openMenu = false"
          />
        </div>
      </button>
      <span
        v-if="openMenu"
        class="fixed w-[190px] shadow-2xl bg-[#282828] rounded-lg top-[52px] right-[35px] z-10 p-1 cursor-pointer"
      >
        <ul class="text-gray-200 font-semibold text-[14px]">
          <li class="px-3 py-2.5 hover:bg-[#3E3D3D] border-b border-b-gray-600">
            Profile
          </li>
          <li class="px-3 py-2.5 hover:bg-[#3E3D3D]">Log out</li>
        </ul>
      </span>
    </div>
    <div id="SideNav" class="h-[100%] p-6 w-[240px] bg-black fixed z-50">
      <RouterLink to="/">
        <img width="125" src="/images/icons/spotify-logo.png" alt="icon logo" />
      </RouterLink>
      <div class="my-8"></div>
      <ul>
        <RouterLink to="/">
          <MenuItem
            class="ml-1.5"
            :iconSize="23"
            name="Home"
            iconString="home"
            pageUrl="/"
          />
        </RouterLink>
        <RouterLink to="/search">
          <MenuItem
            class="ml-1.5"
            :iconSize="23"
            name="Search"
            iconString="search"
            pageUrl="/search"
          />
        </RouterLink>
        <RouterLink to="/library">
          <MenuItem
            class="ml-1.5"
            :iconSize="23"
            name="Library"
            iconString="library"
            pageUrl="/library"
          />
        </RouterLink>
        <div class="py-3.5"></div>
        <MenuItem
          class="ml-1.5"
          :iconSize="23"
          name="Create Playlist"
          iconString="playlist"
          pageUrl="/playslist"
        />
        <MenuItem
          class="ml-1.5"
          :iconSize="23"
          name="Liked Songs"
          iconString="liked"
          pageUrl="/liked"
        />
      </ul>
      <div class="border-b border-b-gray-700"></div>

      <ul>
        <li
          class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white"
        >
          My Playlist #1
        </li>
        <li
          class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white"
        >
          My Playlist #2
        </li>
        <li
          class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white"
        >
          My Playlist #3
        </li>
        <li
          class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white"
        >
          My Playlist #4
        </li>
        <li
          class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white"
        >
          My Playlist #5
        </li>
      </ul>
    </div>
  </div>
</template>
