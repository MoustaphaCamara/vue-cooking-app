<template>
  <div class="meal-container">
    <MealCard :meals="meals" />
  </div>
</template>

<script>
import MealCard from "./MealCard.vue";
export default {
  name: "MealList",
  components: {
    MealCard,
  },
  props: {
    meals: Array,
  },
};
</script>

<style>
.meal-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  background: var(--bgcolor3);
  /* border: 1px solid var(--fontcolor); */
  margin-top: 30px;
}
</style>
