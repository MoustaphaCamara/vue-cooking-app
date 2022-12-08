<template>
  <div v-for="meal in meals" class="meal" :key="meal.idMeal">
    <h2>{{ meal.strMeal }}</h2>
    <h3>
      Origin : <span class="origin">{{ meal.strArea }}</span>
    </h3>
    <img
      class="picture"
      v-bind:src="meal.strMealThumb"
      :alt="`photo of ` + meal.strMeal"
    />
    <p class="instructions">{{ meal.strInstructions }}</p>
  </div>
</template>

<script>
export default {
  name: "MealCard",
  props: {
    meals: Array,
  },
};
</script>

<style scoped>
* {
  font-weight: lighter;
}
.meal {
  flex: 1 0 25%;
  min-width: 200px;
  max-width: 280px;
  background: var(--bgcolor2);
  border: 1px solid var(--gray1);
  margin: 0.5rem;
  padding: 0.5rem;
  position: relative;
  overflow: hidden;
}
.meal::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to top, black, transparent 8%);
  pointer-events: none;
  transition: 2s ease;
}
.meal:hover::after {
  top: 40px;
}

h2 {
  text-shadow: 0 0 5px lightpink;
}
.origin {
  color: lightpink;
}
.picture {
  width: 100%;
  border-radius: 8px;
  transition: 0.2s ease;
}
.picture:hover {
  box-shadow: 0 0 5px white;
  border-radius: 16px;
}
.instructions {
  display: -webkit-box;
  height: 6rem;
  /* -webkit-line-clamp: 4; */
  -webkit-box-orient: vertical;
  overflow-y: scroll;
  overflow-x: hidden;
}

::-webkit-scrollbar {
  width: 10px;
}
::-webkit-scrollbar-track {
  background: black;
}
::-webkit-scrollbar-thumb {
  background: var(--gray1);
}
::-webkit-scrollbar-thumb:hover {
  background: var(--gray2);
}
</style>
