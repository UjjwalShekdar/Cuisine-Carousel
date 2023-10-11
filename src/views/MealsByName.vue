<template>
  <div class="p-8 pb-0">
    <input type="text" v-model="keyword" class="rounded border-2 bg-white border-gray-200 w-full" placeholder="Search for meals"
      @change="searchMeals" />

  </div>
  <Meals :meals="meals" />
</template>

<script setup>

import { RouterLink, useRoute } from 'vue-router';
import store from '../store';
import { ref, computed, onMounted } from 'vue';
import YouTubeButton from '../components/YouTubeButton.vue';
import MealItem from '../components/MealItem.vue';
import Meals from '../components/Meals.vue';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  if(keyword.value){
  store.dispatch('searchMeals', keyword.value)
  }else {
    store.commit("setSearchedMeals", []);
  }
}

onMounted(() => {
  keyword.value = route.params.name //searching by typing in url.
  if (keyword.value) {  //meals appearing as per keyword.
    searchMeals()
  }
})
</script>