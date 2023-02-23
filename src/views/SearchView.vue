<script setup>
import CategorySelect from '../components/CategorySelect.vue';
</script>

<template>
  <div class="p-8">
    <button
      type="button"
      class="text-2xl font-semibold text-white cursor-pointer hover:underline"
    >
      Podcast to make your life better
    </button>

    <div class="py-1.5">
      <div
        class="grid gap-6 xl:grid-cols-5 lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2"
      >
        <CategorySelect
          category="Podcasts"
          image="https://picsum.photos/id/40/300/300"
        />
        <CategorySelect
          category="Podcasts"
          image="https://picsum.photos/id/42/300/300"
        />
        <CategorySelect
          category="Podcasts"
          image="https://picsum.photos/id/43/300/300"
        />
        <CategorySelect
          category="Podcasts"
          image="https://picsum.photos/id/44/300/300"
        />
        <CategorySelect
          category="Podcasts"
          image="https://picsum.photos/id/45/300/300"
        />
        <CategorySelect
          category="Audiobooks"
          image="https://picsum.photos/id/50/300/300"
        />
        <CategorySelect
          category="Audiobooks"
          image="https://picsum.photos/id/52/300/300"
        />
        <CategorySelect
          category="Audiobooks"
          image="https://picsum.photos/id/53/300/300"
        />
        <CategorySelect
          category="Audiobooks"
          image="https://picsum.photos/id/5/300/300"
        />
        <CategorySelect
          category="Audiobooks"
          image="https://picsum.photos/id/55/300/300"
        />
      </div>
    </div>
  </div>
</template>
