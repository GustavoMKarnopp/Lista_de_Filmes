<template>
    <div>
        <h2>Editar filmes</h2>

        <div class="form-group">
            <label > Título: </label>
            <input 
                type="text"
                class="form-control"
                placeholder="Inserir título"
                :value="filmeSelecionado.titulo"
                >

            <input 
                type="text"
                class="form-control"
                placeholder="Inserir ano"
                :value="filmeSelecionado.ano"
                >
            
        </div>
    </div>
</template>
<script>
export default {
    props: {
        filme: {
            type: Object,
            required: true
        }
    },
    data (){
        return{
            filmeLocal :this.filme
        }
    },
    computed:{
        filmeSelecionado: {
            set(dados){
                this.filmeLocal = Object.assign(
                    {},
                    this.filmeLocal,
                    { [dados.propriedade]: dados.valor }
                )
            },
            get(){
                return this.filme
            }
            
        }
    }
}
</script>scr
<style>
.btn{
    float: right;
}
</style>