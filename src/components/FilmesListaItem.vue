<template>
        <li class="list-group-item">
        <span>{{filme.id}} | {{filme.titulo}} | {{filme.diretor}} | {{filme.ano}}</span>
        <button @click="selecionar" class="btn btn-secondary float: right;">Selecionar</button>
    </li>
   
</template>
<script>
import {eventBus} from './../main'
export default {
    
    props:{
       filme: {
           type: String,
           required: true
       }
        
    },
    methods:{
        selecionar() {
        // eventBus.$emit('selecionarFilme', this.filme);
        //this.$emit('selecionarFilme', this.filme);
        eventBus.selecionarFilme(this.filme)
        }
    }
}
</script>
<style scoped>
.btn{
    float: right;
}
</style>