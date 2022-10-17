<template>
    <div class="h100 p-5 bg-light border rounded-3">

        <h2>Pesquisar vagas</h2>
        <div class="row">
        <div class="col">
            <div class="form-group">
            <label>Titulo da vaga</label>
            <input type="text" class="form-control" placeholder="Pesquise sobre as vagas" v-model="titulo">
            <small class="form-text text-muted">Informe palavras que estejam relacionada com a vaga que você procura</small>
            </div>
        </div>
        </div>
        <div class="row">
            <div class="col">
                <button type="button" class="btn btn-outline-dark" @click="pesquisarvaga">Buscar</button>
            </div>
        </div>
    </div>
</template>
<script>
export default{
    name: 'PesquisarVaga',
    data:() =>({
        titulo: ''
    }),
    methods:{
        pesquisarvaga(){
            this.emitter.emit('filtrarVagas', {titulo: this.titulo})
        }
    }
}
</script>