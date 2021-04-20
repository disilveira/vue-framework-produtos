<template>
  <div>
    <div class="input-group mb-3" style="padding-top: 31px">
      <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon1"><b-icon icon="search"></b-icon></span>
      </div>
      <input
        type="text"
        class="form-control"
        placeholder="Pesquisar Produto"
        v-model="pesquisar"
      />
    </div>
    <ProductItem
      v-for="produto in produtos"
      :key="produto.nome"
      :produto="produto"
    />
    <p class="text-center">
      <strong>{{ totalProdutos }}</strong> produto(s) cadastrado(s)
    </p>
  </div>
</template>

<script>
import ProductItem from "./ProductItem";

export default {
  data() {
      return {
          produtoFiltrado: [],
          todosOsProdutos: [],
          pesquisar: ""
      };
  },
  components: {
    ProductItem,
  },
  props: {
    produtos: Array,
  },
  computed: {
    totalProdutos: function () {
      return this.produtos.length;
    },
  },
  watch: {
      pesquisar: function (valor){
          valor = valor.toLowerCase();
          if(this.todosOsProdutos.length === 0){
              this.todosOsProdutos = this.produtos;
          }

          this.produtos = this.produtos.filter(item => item.nome.toLowerCase().indexOf(valor) !== -1);

          if(valor.length === 0){
              this.produtos = this.todosOsProdutos
          }
      }
  }
};
</script>