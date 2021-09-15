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
                >

            <input 
                type="text"
                class="form-control"
                placeholder="Inserir ano"
                :value="filme.ano"
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
}
</script>scr
<style>
.btn{
    float: right;
}
</style>