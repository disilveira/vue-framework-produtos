<template>
  <div id="app">
    <Nav titulo="Cadastro de Produtos - Vue" />
    <div class="container">
      <div class="row">
        <div class="col-md-5">
          <ProductForm :onAddProduto="handleOnAddProduct" />
        </div>
        <div class="col-md-7">
          <ProductList :produtos="produtos" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Nav from "./components/Nav";
import ProductForm from "./components/ProductForm";
import ProductList from "./components/ProductList";

export default {
  data() {
    return {
      produtos: [
        {
          nome: "Iphone 12",
          preco: "4.500,00",
          categoria: "Celular",
        },
        {
          nome: "Playstation 5",
          preco: "7.500,00",
          categoria: "Console",
        },
      ],
    };
  },
  components: {
    Nav,
    ProductForm,
    ProductList,
  },
  methods: {
    handleOnAddProduct(produto) {
      this.produtos = this.produtos.concat(produto);
    },
  },
};
</script>