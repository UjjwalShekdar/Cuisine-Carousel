<template>
  <div class="bg-white shadow rounded-xl">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-xl w-full h-64 object-cover" />
    </router-link>


    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="mb-4">
        It is a long established fact that a reader will be distracted by the readable content of a page when looking at
        its layout.
      </p>
      <div class="flex items-center justify-between">
        <YouTubeButton :href="meal.strYoutube">
          YouTube
        </YouTubeButton>
        <!-- <router-link to="/" class="px-3 py-2 rounded border-2 
              border-purple-600 bg-purple-500 hover:bg-purple-600 
              text-white transition-colors">
            View
          </router-link> -->

        <ViewOriginalSource :href="meal.strSource">
          View Source
        </ViewOriginalSource>
      </div>

    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import YouTubeButton from './YouTubeButton.vue';
import ViewOriginalSource from './ViewOriginalSource.vue';

const { meal } = defineProps({
  meal: {
    required: true,
    type: Object
  }
});
</script>