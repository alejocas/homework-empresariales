<template>
    <div>
        <form>
            <input type="text" name="valueSearched" v-model="query">
            <button type="submit" @click="searchItem">Buscar</button>
        </form>
        <div class="item" v-for="item in items" :key="item">
            <!-- Aquí van las tarjetas con productos. -->
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
  mounted() {},
  methods: {
    searchItem(e) {
      e.preventDefault();
      if (this.query != "") {
        axios({
          method: "GET",
          url: `https://api.mercadolibre.com/sites/MCO/search?q=${this.query}`
        }).then(
          result => {
            this.items = result.data.results;
          },
          error => {
            this.items = error;
          }
        );
        this.query = "";
      }
    }
  }
};
</script>

<style lang="scss">
.item {
}
</style>
