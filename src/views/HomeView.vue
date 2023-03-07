<script setup>
import HomeCard from '../components/HomeCard.vue';
import { ref } from 'vue';
let rows = ref([
  {
    title: 'Podcast to make your life better',
    list: [
      {
        image: 'https://picsum.photos/id/15/300/300',
        title: 'Dare',
        subtitle: 'You can become who you want to be',
      },
      {
        image: 'https://picsum.photos/id/22/300/300',
        title: 'Walk and learn',
        subtitle: '100 lessons to listen on your commute',
      },
      {
        image: 'https://picsum.photos/id/49/300/300',
        title: 'Grinding at the windmills',
        subtitle: 'From grain to flour',
      },
      {
        image: 'https://picsum.photos/id/124/300/300',
        title: 'Nomad lowtech',
        subtitle: 'lowtech life on a boat',
      },
    ],
  },
  {
    title: 'Recommended Radio',
    list: [
      {
        image: 'https://picsum.photos/id/31/300/300',
        title: 'Radio Feet',
        subtitle: 'Smelling and listening',
      },
      {
        image: 'https://picsum.photos/id/28/300/300',
        title: 'Natural Ambiance',
        subtitle: 'Relax and focus',
      },
      {
        image: 'https://picsum.photos/id/77/300/300',
        title: 'Holidays',

        subtitle: 'Bring it on',
      },
      {
        image: 'https://picsum.photos/id/78/300/300',
        title: 'Church Bells',
        subtitle: 'Best Bells Melodies',
      },
    ],
  },
  {
    title: 'Podcast to make you smarter',
    list: [
      {
        image: 'https://picsum.photos/id/3/300/300',
        title: 'Smartest way to make your life better',
        subtitle: 'a podcast to make your life better',
      },
      {
        image: 'https://picsum.photos/id/84/300/300',
        title: '30 ways to make money',
        subtitle: 'a podcast to make you richer',
      },
      {
        image: 'https://picsum.photos/id/57/300/300',
        title: 'Ten rules of making friends',
        subtitle: 'never be alone anymore',
      },
      {
        image: 'https://picsum.photos/id/7/300/300',
        title: 'Rise up',
        subtitle: 'how to ask your boss for a rise',
      },
    ],
  },
  {
    title: 'Recommended Songs',
    list: [
      {
        image: 'https://picsum.photos/id/30/300/300',
        title: '100% Arabica',
        subtitle: 'The Coffee Machines',
      },
      {
        image: 'https://picsum.photos/id/45/300/300',
        title: 'Tck - The Truck',

        subtitle: 'TCK band',
      },
      {
        image: 'https://picsum.photos/id/65/300/300',
        title: 'Sunny Phillips',
        subtitle: 'Lena Ringa',
      },
      {
        image: 'https://picsum.photos/id/67/300/300',
        title: 'Montains of gold',
        subtitle: 'Johannes Verne',
      },
    ],
  },
]);

const props = defineProps({
  rows: [
    {
      title: String,
      list: [{ image: String, title: String, subtitle: String }],
    },
  ],
});
</script>

<template>
  <main>
    <div class="p-8">
      <div v-for="row in rows">
        <button
          type="button"
          class="text-2xl font-semibold text-white cursor-pointer hover:underline"
        >
          {{ row.title }}
        </button>

        <div class="py-1.5">
          <div class="flex items-center">
            <HomeCard
              v-for="{ image, title, subtitle } in row.list"
              :image="image"
              :title="title"
              :subtitle="subtitle"
              class="hidden md:block"
            />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
