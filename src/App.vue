<template>
  <div id="header">
    <h1>Food</h1>
    <p>Components created with v-for based on an array.</p>
  </div>
  <div id="wrapper">
    <food-item
      v-for="x in foods"
      :key="x.name"
      v-bind:food-name="x.foodName"
      v-bind:is-favorite="x.isFavorite"
      v-bind:food-price="x.foodPrice"
      @toggle-favorite="receiveEmit"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      foods: [
        {
          foodName: "Apples",
          foodPrice: 4.5,
          isFavorite: true,
        },
        {
          foodName: "Pizza",
          foodPrice: 2.0,
          isFavorite: false,
        },
        {
          foodName: "Caje",
          foodPrice: 3.5,
          isFavorite: false,
        },
      ],
    };
  },
  methods: {
    // receiveEmit({ foodName, isFavorite }) {
    //   alert(`${foodName} favorite status switched to: ${isFavorite}`);
    // },
    receiveEmit(foodName) {      
      const foundFood = this.foods.find((food) => food.foodName === foodName);      
      foundFood.favorite = !foundFood.favorite;
      alert(`${foodName} favorite status switched to: ${foundFood.favorite}`);
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}

#app {
  box-sizing: border-box;
  min-height: 100vh;
  min-width: 100vw;

  display: inline-flex;
  flex-flow: column nowrap;
  justify-content: flex-start;
  align-items: center;
  gap: 1.5rem;

  padding: 1rem;
}

#wrapper {
  display: flex;
  gap: 0.5rem;
}

#wrapper > div,
#header {
  border: dashed black 1px;
  background-color: lightgreen;
  padding: 0.5rem;
}
</style>
