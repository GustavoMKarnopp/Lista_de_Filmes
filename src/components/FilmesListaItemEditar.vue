<template>
    <div>
        <h2>Editar filmes</h2>

        <div class="form-group">
            <label > Título: </label>
            <input 
                type="text"
                class="form-control"
                placeholder="Inserir título"
                :value="filme.titulo"
                @input="filmeSelecionado = { propriedade: 'titulo', valor: $event.target.value }"
                >

            <input 
                type="text"
                class="form-control"
                placeholder="Inserir ano"
                :value="filme.ano"
                @input="filmeSelecionado = { propriedade: 'ano', valor: $event.target.value }"

                >
            
        </div>

            <button @click="salvarFilme" class="btn btn-primary float-right"> Salvar </button>
    </div>
</template>
<script>
import {eventBus} from '../main'
export default {
    props: {
        filme: {
            type: Object,
            required: true
        }
    },
    data(){
        return{
            filmeLocal: this.filme
        }
    }, 
    computed:{
        filmeSelecionado:{
            set(dados){
                this.filmeLocal = Object.assign(
                    {},
                    this.filmeLocal,
                    { [dados.propriedade] : dados.valor }
                    )
            },
            get(){
                return this.filme
            }
        },
        
    },
    methods:{
        salvarFilme(){
        eventBus.atualizarFilme(this.filmeLocal)
        }
    }

}
</script>scr
<style>
.btn{
    float: right;
}
</style>