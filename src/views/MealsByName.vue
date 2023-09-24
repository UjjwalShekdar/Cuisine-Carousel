<template>
  <div class="p-8 pb-0">
    <input type="text" v-model="keyword" class="rounded border-2 border-gray-200 w-full" placeholder="Search for meals"
      @change="searchMeals" />

  </div>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-8 p-8">
    <div v-for="meal of meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">
      <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
        <img :src="meal.strMealThumb" :alt="strMeal" class="rounded-t-xl w-full h-64 object-cover" />
      </router-link>


      <div class="p-3">
        <h3 class="font-bold">{{ meal.strMeal }}</h3>
        <p class="mb-4">
          It is a long established fact that a reader will be distracted by the readable content of a page when looking at
          its layout.
        </p>
        <div class="flex items-center justify-between">
          <YouTubeButton :href="meal.strYoutube"/>
          <!-- <router-link to="/" class="px-3 py-2 rounded border-2 
              border-purple-600 bg-purple-500 hover:bg-purple-600 
              text-white transition-colors">
            View
          </router-link> -->
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>

import { RouterLink, useRoute } from 'vue-router';
import store from '../store';
import { ref, computed, onMounted } from 'vue';
import YouTubeButton from '../components/YouTubeButton.vue';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch('searchMeals', keyword.value)
}

onMounted(() => {
  keyword.value = route.params.name //searching by typing in url.
  if (keyword.value) {  //meals appearing as per keyword.
    searchMeals()
  }
})
</script>