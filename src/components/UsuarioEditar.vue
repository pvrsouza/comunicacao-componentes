<template>
  <div class="componente">
    <h2>Alterar os Dados de Usuário</h2>
    <p>Edite as informações</p>
    <p>Idade do usuário: {{idadeUsuario}}</p>
    <button @click="alterarIdade">Alterar Idade</button>
  </div>
</template>

<script>
import barramento from "@/barramento";

export default {
  props: {
    idade: Number
  },
  data() {
    return {
      idadeUsuario: this.idade
    };
  },
  methods: {
    alterarIdade() {
      this.idadeUsuario++;
      //this.$emit("idadeMudou", 33);
      //barramento.$emit("idadeMudou", this.idadeUsuario);
      barramento.alterarIdade(this.idadeUsuario);
    }
  }
};
</script>

<style scoped>
.componente {
  flex: 1;
  background-color: #98b99a;
  color: #fff;
}
</style>
