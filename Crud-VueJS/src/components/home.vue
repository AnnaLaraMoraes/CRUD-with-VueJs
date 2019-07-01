<template>
  <div>
    <div id="add_btn" class="container">
      <div class="row">
        <div class="col-9">
          <b-form-input
            id="search"
            size="sm"
            class="mr-sm-2 search"
            placeholder="Digite aqui para buscar..."
          ></b-form-input>
          <b-button
            size="sm"
            class="my-2 my-sm-0 search"
            type="submit"
            variant="outline-secondary"
          >Buscar</b-button>
        </div>
        <div class="col-3">
          <b-button
            size="sm"
            class="my-2 my-sm-0"
            variant="outline-primary"
            v-b-modal.modal-prevent-closing
          >Cadastrar</b-button>
        </div>
      </div>
    </div>
    <Products v-bind:products="products" v-on:del-product="deleteProduct" />

    <b-modal
      id="modal-prevent-closing"
      ref="modal"
      title="Cadastro de Produtos"
      @show="resetModal"
      @hidden="resetModal"
      @ok="handleOk"
      centered
    >
      <form ref="form" @submit.stop.prevent="handleSubmit">
        <b-form-group
          :state="state"
          label="Nome"
          label-for="name-input"
          invalid-feedback="Nome é obrigatório"
        >
          <b-form-input id="name-input" v-model="name" :state="state" required></b-form-input>
        </b-form-group>
        <b-form-group
          :state="state"
          label="Descrição"
          label-for="description-input"
          invalid-feedback="Descrição é obrigatório"
        >
          <b-form-input id="description-input" v-model="description" :state="state" required></b-form-input>
        </b-form-group>
        <b-form-group
          :state="state"
          label="Preço"
          label-for="price-input"
          invalid-feedback="Preço é obrigatório"
        >
          <b-form-input id="price-input" v-model="price" :state="state" required></b-form-input>
        </b-form-group>
        <b-form-group
          :state="state"
          label="Imagem"
          label-for="image-input"
          invalid-feedback="Imagem é obrigatória"
        >
          <b-form-input id="image-input" v-model="image" :state="state" required></b-form-input>
        </b-form-group>
      </form>
    </b-modal>
  </div>
</template>

<script>
import Products from "./products";

export default {
  name: "Home",
  components: {
    Products
  },
  data() {
    return {
      name: "",
      description: "",
      price: 0.0,
      image: "",
      state: null,

      products: []
    };
  },
  methods: {
    deleteProduct(id) {},
    checkFormValidity() {
      const valid = this.$refs.form.checkValidity();
      this.state = valid ? "valid" : "invalid";
      return valid;
    },
    resetModal() {
      this.name = "";
      this.state = null;
    },
    handleOk(bvModalEvt) {
      bvModalEvt.preventDefault();
      this.handleSubmit();
    },
    handleSubmit() {

      if (!this.checkFormValidity()) {
        return;
      }

      console.log('passou');

      let newProduct = {
        name: this.name,
        description: this.description,
        price: this.price,
        image: this.image
      };
      //aqui seria o post para o servidor
      this.products.push(newProduct);

      this.$nextTick(() => {
        this.$refs.modal.hide();
      });
    }
  }
};
</script>

<style>
footer {
  display: block;
}
#add_btn {
  padding: 30px;
  border-width: 0.2rem 0 0;
  text-align: right;
}
#search {
  width: 50%;
  display: inline;
}
.modal-backdrop {
  background-color: rgba(0, 0, 0, 0.473);
}
</style>
