<template>
  <div class="componente">
    <h2>As Informações de Usuário</h2>
    <p>Vários detalhes...</p>
    <p>
      Nome do usuário:
      <strong>{{ inverterNome() }}</strong>
    </p>
    <p>
      Idade do usuário:
      <strong>{{idadeUsuario}}</strong>
    </p>
  </div>
</template>

<script>
import barramento from "@/barramento";
export default {
  props: {
    nome: {
      type: String,
      //required: true
      default: "Anônimo" //caso
    },
    idade: {
      type: Number
    }
  },
  data() {
    return {
      idadeUsuario: this.idade
    };
  },
  methods: {
    inverterNome() {
      return this.nome
        .split("")
        .reverse()
        .join("");
    }
  },
  created() {
    /*barramento.$on("idadeMudou", idade => {
      this.idadeUsuario = idade;
    });*/
    barramento.quandoIdadeMudar(idade => {
      this.idadeUsuario = idade
    })
  }
};
</script>

<style scoped>
.componente {
  flex: 1;
  background-color: #ec485f;
  color: #fff;
}
</style>
