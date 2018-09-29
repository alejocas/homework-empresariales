<template>
    <div class="card">
        <img :src="thumbnail" alt="Miniatura del producto" height="35%" width="35%">
        <div class="container">
            <p><b>Producto:</b>{{title}}</p> 
            <p>Precio:{{price}} COP</p> 
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
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  color: #1259C3;
}

.container {
  padding-bottom:16px;
  padding-left: 3px;
  padding-right: 3px;
}
</style>
