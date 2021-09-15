<template>
    <div class="row">

        <!-- Coluna 01 -->
        <div class="col-8">
            
            <h2>Filmes</h2>

            <ul class="list-group lista-group-flush">
                <FilmesListaItem
                :class="aplicarClasseActiva(filme)"
                v-for="filme in filmes"
                :key="filme.id"
                :filme="filme"
                @selecionarFilme="filmeSelecionado = $event"
                />          
            </ul>
        </div>
        <!-- Coluna 02 -->

        <div class="col-4">
            <FilmesListaItemInfo
             :filme="filmeSelecionado"
             @editarFilme="editarFilme"/>
        </div>
    </div>
</template>

<script>

import FilmesListaItem from './FilmesListaItem.vue';
import FilmesListaItemInfo from './FilmesListaItemInfo.vue';

export default {
    components:{
        FilmesListaItem,
        FilmesListaItemInfo
    },
    data (){
        return{
            filmes: [   
                {id: 1, titulo : 'Vingadores: Guerra Infinita', ano:2018, diretor: 'Gustavo Karnopp'},
                {id: 2 , titulo :'Homem formiga e a Vesta ', ano:2018, diretor: 'Gustavo Karnopp' },
                {id: 3, titulo: 'Pantera Negra', ano:2018, diretor: 'Gustavo Karnopp'}
            ],
            filmeSelecionado: undefined,
            editar: false
        }
    },
    methods:{
        aplicarClasseActiva(filmeIterado){
            return {
                active:this.filmeSelecionado && this.filmeSelecionado.id === filmeIterado.id
            }

        },
        editarFilme(filme){
            this.editar = true
            this.filmeSelecionado = filme
        }
    }
}
</script>