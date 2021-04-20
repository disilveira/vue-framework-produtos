<template>
  <div>
    <form @submit.prevent="onFormSubmit">
      <div class="form-group">
        <label for="nome"><strong>Produto</strong></label>
        <input
          type="text"
          class="form-control"
          v-model="nome"
          placeholder="Digite o nome do Produto"
        />
        <small class="text-danger"><strong>{{isProductNameLimitExceeded}}</strong></small>
      </div>
      <div class="form-group">
        <label for="nome"><strong>Preço</strong></label>
        <input
          type="text"
          class="form-control"
          v-model="preco"
          placeholder="Digite o preço do Produto"
        />
      </div>
      <div class="form-group">
        <label for="nome"><strong>Categoria</strong></label>
        <input
          type="text"
          class="form-control"
          v-model="categoria"
          placeholder="Digite a categoria do Produto"
        />
      </div>
      <nav aria-label="breadcrumb">
        <ol class="breadcrumb">
          <li class="breadcrumb-item active" aria-current="page">
            <strong>Produto:</strong> {{ nome }} <br/> 
            <strong>Preço:</strong> {{ preco }} <br/> 
            <strong>Categoria:</strong> {{ categoria }}
          </li>
        </ol>
      </nav>
      <button type="submit" class="btn btn-success btn-block">Cadastrar</button>
    </form>

  </div>
</template>

<script>


export default {
  data() {
    return {
      nome: "",
      preco: "",
      categoria: "",
      isProductNameLimitExceeded: ""
    };
  },
  props: {
    onAddProduto: Function,
  },
  methods: {
    onFormSubmit() {
      const produto = {
        nome: `${this.nome}`,
        preco: `${this.preco}`,
        categoria: `${this.categoria}`,
      };

      this.onAddProduto(produto);
    },
  },
  watch: {
      nome(){
          if(this.nome.length > 15){
              this.isProductNameLimitExceeded = "O Produto ultrapassou o limite de 15 caracteres"
          } else {
              this.isProductNameLimitExceeded = ""
          }
      }
  }
};
</script>