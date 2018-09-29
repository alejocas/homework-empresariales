<template>
    <div class="card">
        <img :src="thumbnail" alt="Miniatura del producto" style="width:100%">
        <div class="container">
            <h4><b>{{title}}</b></h4> 
            <p>{{price}}</p> 
        </div>
    </div>
</template>

<script>
export default {
  name:"ItemCard",
  data() {
    return {};
  },
  props: {
    title: String,
    price: Number,
    thumbnail: String
  }
};
</script>

<style scoped lang="scss">
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  width: 10%;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

.container {
  padding: 2px 16px;
}
</style>
