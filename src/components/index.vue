<template>
  <div class="index">
    <form >
      <div>
        <input type="text" v-model="parametroBusca" placeholder="Busca Linha">
        <button type="submit" v-on:click.prevent="buscaLinha(parametroBusca)">Buscar</button>
      </div>
    </form>
    <div>
      <button type="submit" v-on:click.prevent="listaEmpresas()">Listar</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'index',
  data () {
    return {
      msg: 'Nova Página Vue.js App',
      parametroBusca: ''
    }
  },
  methods: {
    acessoApi () {
      this.$http({
        url: 'http://api.olhovivo.sptrans.com.br/v2.1/Login/Autenticar',
        method: 'post',
        params: {
          token: '3630e442b68893f13e4f15b11391cf67c4dab3f9200ecbc5b01bc040c9e94cb9'
        }
      })
        .then((response) => {
        console.log(response.data);
      })
    },
    buscaLinha (parametro) {
      this.$http({
        url: 'http://api.olhovivo.sptrans.com.br/v2.1/Linha/Buscar',
        method: 'get',
        params: {
          termosBusca: parametro
        }
      })
        .then((response) => {
          console.log(response.data);
        })
    },
    listaEmpresas () {
      this.$http({
        url: 'http://api.olhovivo.sptrans.com.br/v2.1/Empresa',
        method: 'get'
      })
        .then((response) => {
          console.log(response.data);
        })
    }
  },
  mounted () {
    this.acessoApi();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
