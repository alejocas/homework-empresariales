<template>
    <div>
        <form>
            <input type="text" name="valueSearched" v-model="query">
            <button type="submit" @click="searchItem">Buscar</button>
        </form>
        <!-- Aquí van las tarjetas con productos. -->
        <ul>
            <li v-for="item in items" :key="item">
                <ItemCard 
                :title="item.title" 
                :price="item.price" 
                :thumbnail="item.thumbnail">
                </ItemCard>
            </li>
        </ul>
    </div>
</template>

<script>
import axios from "axios";
import ItemCard from "./ItemCard.vue";

export default {
  name: "Shop",
  data() {
    return {
      query: "",
      items: []
    };
  },
  components: {
    ItemCard
  },
  methods: {
    searchItem(e) {
      e.preventDefault();
      if (this.query != "") {
        axios({
          method: "GET",
          url: `https://api.mercadolibre.com/sites/MCO/search?q=${this.query}&limit=5`
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
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
