<template>
    <div>
        <div class="vagafavorita">
            <button class="btn btn-outline-light" type="button" data-bs-toggle="offcanvas" data-bs-target="#staticBackdrop" aria-controls="staticBackdrop">Vagas Favoritas</button>
        </div>

        <div class="offcanvas offcanvas-start" data-bs-backdrop="static" tabindex="-1" id="staticBackdrop" aria-labelledby="staticBackdropLabel">
            <div class="offcanvas-header">
                <h5 class="offcanvas-title" id="staticBackdropLabel">Suas vagas favoritadas</h5>
                <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
            </div>
        <div class="offcanvas-body">
            <ol class="list-group list-group-numbered">
                <li class="list-group-item" v-for="(vaga, index) in vagas" :key="index">{{vaga}}</li>
            </ol>
        </div>
</div>
    </div>  
</template>

<script>
export default {
    name: "VagasFavorita",
    data:() => ({
        vagas: []
    }),
    mounted() {
        this.emitter.on('favoritarVaga', (titulo) =>{
           this.vagas.push(titulo)
        })
        this.emitter.on('desfavoritarVaga', (titulo) =>{
            let indiceArray = this.vagas.indexOf(titulo)
            if(indiceArray !== -1) this.vagas.splice(indiceArray, 1)
        })
    }
}
</script>
<style scoped>
    .vagafavorita{
        position:absolute; 
        z-index:1; 
        top:10px; 
        right:5px
    }
</style>