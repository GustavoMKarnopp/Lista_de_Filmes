<template>
    <div class="row">

        <div class="col-8">
            
            <h2>Filmes</h2>

        <!-- Coluna 01 -->
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
                v-if="!editar"    
                :filme="filmeSelecionado"
                @editarFilme="editarFilme"/>
            <FilmesListaItemEditar
                v-else
                :filme="filmeSelecionado"
            />
        </div>
    </div>
</template>

<script>
import {eventBus} from '../main'

import FilmesListaItem from './FilmesListaItem.vue';
import FilmesListaItemEditar from './FilmesListaItemEditar.vue';
import FilmesListaItemInfo from './FilmesListaItemInfo.vue';

export default {
    components:{
        FilmesListaItem,
        FilmesListaItemEditar,
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
    },
    created() {
        eventBus.$on('selecionarFilme',(filmeSelecionado) => {
            this.filmeSelecionado = filmeSelecionado
        })
    }
}
</script>