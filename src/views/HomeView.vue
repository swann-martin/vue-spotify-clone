<script setup>
import HomeCard from '../components/HomeCard.vue';
</script>

<template>
  <main>
    <div class="p-8">
      <button
        type="button"
        class="text-2xl font-semibold text-white cursor-pointer hover:underline"
      >
        Podcast to make your life better
      </button>

      <div class="py-1.5">
        <div class="flex items-center">
          <HomeCard
            image="https://picsum.photos/id/30/300/300"
            title="Title"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/45/300/300"
            title="Title"
            class="hidden md:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/65/300/300"
            title="Title"
            class="hidden lg:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/67/300/300"
            title="Title"
            class="hidden xl:block"
            subtitle="subtitle is here"
          />
        </div>
      </div>
    </div>
    <div>
      <button
        type="button"
        class="text-2xl font-semibold text-white cursor-pointer hover:underline"
      >
        Recommended Radio
      </button>

      <div class="py-1.5">
        <div class="flex items-center">
          <HomeCard
            image="https://picsum.photos/id/30/300/300"
            title="Title"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/45/300/300"
            title="Title"
            class="hidden md:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/65/300/300"
            title="Title"
            class="hidden lg:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/67/300/300"
            title="Title"
            class="hidden xl:block"
            subtitle="subtitle is here"
          />
        </div>
      </div>
    </div>
    <div>
      <button
        type="button"
        class="text-2xl font-semibold text-white cursor-pointer hover:underline"
      >
        Podcast to make you smarter
      </button>

      <div class="py-1.5">
        <div class="flex items-center">
          <HomeCard
            image="https://picsum.photos/id/30/300/300"
            title="Title"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/45/300/300"
            title="Title"
            class="hidden md:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/65/300/300"
            title="Title"
            class="hidden lg:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/67/300/300"
            title="Title"
            class="hidden xl:block"
            subtitle="subtitle is here"
          />
        </div>
      </div>
    </div>
    <div>
      <button
        type="button"
        class="text-2xl font-semibold text-white cursor-pointer hover:underline"
      >
        Recommended Songs
      </button>

      <div class="py-1.5">
        <div class="flex items-center">
          <HomeCard
            image="https://picsum.photos/id/30/300/300"
            title="Title"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/45/300/300"
            title="Title"
            class="hidden md:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/65/300/300"
            title="Title"
            class="hidden lg:block"
            subtitle="subtitle is here"
          />
          <HomeCard
            image="https://picsum.photos/id/67/300/300"
            title="Title"
            class="hidden xl:block"
            subtitle="subtitle is here"
          />
        </div>
      </div>
    </div>
  </main>
</template>
