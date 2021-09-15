<template>
      <div>

        <div class="jumbotron jumbotron-fluid">
          <div class="container">
              <h1 class="display-4">Lista de filmes</h1>
              <p class="lead">Treinando Comunicação entre componentes</p>             
        </div>
      </div>

      <div class="container">
        <FilmesLista/>
      </div>

 </div>
</template>

<script>
/*IMPORTAÇÃO DO COMPONENTE */
import FilmesLista from './components/FilmesLista.vue'

export default {
  /*REGISTRO FEITO LOCALMENTE DENTRO DO APP.VUE*/
  components: {
    FilmesLista 
  }
}
</script>

<style>

