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
    <p id="noData">Aucun résultat pour cette recherche..</p>
    <MealList :meals="meals" />
  </div>
  <footer>
    <p>© Moustapha Camara - 2022</p>
  </footer>
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
      if (this.meals == null && this.text !== "") {
        noData.style.display = "block";
      } else {
        noData.style.display = "none";
      }
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
  color: var(--gray2);
  filter: brightness(120%);
}
h3 + p {
  color: var(--gray1);
}
</style>
