<template>
   <Meals :meals="meals" />
</template>

<script setup>
import { onMounted, ref, computed } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue';
import YouTubeButton from '../components/YouTubeButton.vue';
import ViewOriginalSource from '../components/ViewOriginalSource.vue';

const route = useRoute();
const meals = computed(()=> store.state.mealsByIngredient);

onMounted(() => {
  store.dispatch('searchMealsByIngredient', route.params.ingredient)
})
</script>