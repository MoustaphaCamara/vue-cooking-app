<template>
  <h1>{{ title }}</h1>
  <h3>Created with Vite & Vue3</h3>
  <p>Using TheMealDb Api</p>
  <input
    @input="fetchData()"
    type="text"
    name="text"
    v-model="text"
    placeholder="looking for ?"
  />
  <div class="app-container">
    <MealList :meals="meals" />
  </div>
</template>

<script>
import axios from "axios";
import MealList from "./MealList.vue";
export default {
  name: "MainPage",
  methods: {},
  components: {
    MealList,
  },
  data() {
    return {
      meals: null,
      text: "",
    };
  },
  props: {
    title: String,
  },
  methods: {
    fetchData() {
      axios
        .get(
          `https://www.themealdb.com/api/json/v1/1/search.php?s=${this.text}`
        )
        .then((res) => (this.meals = res.data.meals));
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>

<style>
h3 {
  color: #555555;
}
h3 + p {
  color: #454545;
}
</style>
