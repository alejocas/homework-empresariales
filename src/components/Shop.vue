<template>
    <div>
        <form>
            <input type="text" name="valueSearched" v-model="query" placeholder="Busque su producto aquí">
            <button class="btn btn-primary" type="submit" @click="searchItem">Buscar</button>
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
          url: `https://api.mercadolibre.com/sites/MCO/search?q=${this.query}&limit=15`
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

ul {
  text-align: left;
}

li {
  list-style-type: none;
  display: inline-flex;
  width: 15%;
  margin: 1% 1% 1% 1%;
  text-align: center;
  background-color: #FFFFFF;
}
</style>
