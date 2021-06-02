<template>
  <div id="app">
    <!-- <Cadastro /> -->
    <form action="#" method="post">
      <fieldset>
        <fieldset class="grupo">
          <div class="campo">
            <label for="MatriculaEstudante">Matricula estudante: </label>
            <input
              type="text"
              id="MatriculaEstudante"
              name="MatriculaEstudante"
              style="width: 10em"
              value=""
            />
          </div>
          <div class="campo">
            <label for="NomeEstudante">Nome Estudante: </label>
            <input
              type="text"
              id="NomeEstudante"
              name="NomeEstudante"
              style="width: 10em"
              value=""
            />
          </div>
        </fieldset>
        <div class="campo">
          <label for="email">Nome Cliente</label>
          <input
            type="text"
            id="NomeCliente"
            name="NomeCliente"
            style="width: 20em"
            value=""
          />
        </div>
        <div class="campo">
          <label for="EndereçoCliente">Endereço cliente</label>
          <input
            type="text"
            id="EndereçoCliente"
            name="EndereçoClientee"
            style="width: 10em"
            value=""
          />
        </div>

        <fieldset>
          <div>
            <label for="Estado">Estado: </label>
            <div>
              <select>
                <option v-for="(estado, index) in estados" :key="index.id">{{
                  estado.sigla
                }}</option>
              </select>
            </div>
          </div>
          <!-- <div class="campo">
            <label for="Cidade">Cidade</label>
            <select name="Cidade" id="Cidade">
              <option value="">-{{}}</option>
              <option value="PR">P</option>
            </select>
          </div> -->
        </fieldset>
        <button type="submit" name="submit">Cadastrar</button>
      </fieldset>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      estados: [],
    };
  },
  created: function() {
    axios
      .get("https://servicodados.ibge.gov.br/api/v1/localidades/estados")
      .then((res) => {
        this.estados = res.data;
        console.log(this.estados);
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
// v-for="(estado, index) in estados" :key="index.id"
