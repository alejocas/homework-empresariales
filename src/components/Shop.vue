<template>
    <div>
        <form v-on:submit='searchItem'>
            <input type="text" class="form-control" v-model="query">
        </form>
        <div class="item" v-for="item in items" :key="item">
            <!-- Aquí debemos colocar la tarjeta de items. -->
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Shop",
  data() {
    return {
      query: "",
      items: []
    };
  },
  props: {},
  mounted() {
    axios({
      method: "GET",
      url: "https://api.mercadolibre.com/sites/MCO/search?q=Guantes"
    }).then(
      result => {
        this.items = result.data.results;
      },
      error => {
        this.items = error;
      }
    );
  },
  methods: {
    searchItem: e => {
      e.preventDefault();
    }
  }
};
</script>

<style lang="scss">

.item

</style>
