<template>
  <div class="product-item container">
    <div class="row">
      <div class="col-sm-10">
        <p>{{product.name}}</p>
        <p>{{product.description}}</p>
      </div>
      <div class="col-sm-2">
        <button type="button" class="btn btn-outline-warning">Editar</button>
        <button
          type="button"
          class="btn btn-outline-danger"
          @click="$emit('del-product', product.id)"
        >Excluir</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductItem",
  props: ["product"]
};
</script>

<style scoped>
.product-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
</style>