<template>
       <div class="grid grid-cols-1 md:grid-cols-3 gap-8 p-8">
     <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal"/>
   </div>
   <div v-if="!meals.length" class="flex justify-center text-gray-600">
      There is no Meal.
   </div>
</template>

<script setup>
import MealItem from './MealItem.vue';
import YouTubeButton from './YouTubeButton.vue';
import ViewOriginalSource from './ViewOriginalSource.vue';


const {meals} = defineProps({
  meals:{
    required: true,
    type: Array,
  }
});
</script>