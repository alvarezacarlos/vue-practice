<template>
  <div v-on:click="countClicks">
    <h2>{{ name }}</h2>
    <p>{{ message }}</p>
    <p>Price: {{ foodPrice }}</p>
    <p>Favorite: {{ foodIsFavorite }}</p>
    <p id="red">You have clicked me {{ clicks }} times.</p>
    <button @click="toggleFavorite">Favorite</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: this.foodName,
      message: "I like " + this.foodName,
      clicks: 0,
      foodIsFavorite: this.isFavorite,
    };
  },
  methods: {
    countClicks() {
      this.clicks++;
    },
    toggleFavorite() {
      this.foodIsFavorite = !this.foodIsFavorite;
      // this.$emit("toggle-Favorite", {
      //   foodName: this.foodName,
      //   isFavorite: this.foodIsFavorite,
      // });
      this.$emit("toggle-Favorite", this.foodName);
    },
  },
  // props: ['foodName', 'foodPrice'], // not required
  props: {
    foodName: {
      type: String, // type
      required: true, // required
      default: "Orange", // default value
      validator: function (value) {
        // validators
        if (4 <= value.length && value.length < 10) {
          return true;
        } else {
          return false;
        }
      },
    },
    isFavorite: {
      type: Boolean, // type
      default: true, // default value
    },
    foodPrice: {
      type: Number, // type
      default: 4.1, // default value
    },
  },
};
</script>

<style>
#red {
  font-weight: bold;
  color: rgb(144, 12, 12);
}
</style>
