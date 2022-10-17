<template>
    <div class="card">
              <div class="card-header bg-dark text-white">
                <div class="row">
                  <div class="col d-flex justify-content-between">
                    <div>
                      {{titulo}}
                    </div>
                    <div>
                      <div class="form-check form-switch">
                        <input class="form-check-input" type="checkbox" v-model="favoritada">
                        <label class="form-check-label">Favoritar </label>
                      </div>
                    </div>
                  </div>
                </div>

              </div>
              <div class="card-body">
                <p>{{descricao}}</p>
              </div>
              <div class="card-footer">
                <small class="text-muted">Salario: {{salario}} | Modalidade: {{getmodalidade}} | Tipo: {{gettipo}} | Publicação: {{getpublicacao}} </small>
              </div>
            </div>
</template>

<script>
    export default{
        name: 'Vaga',
        data: () => ({
          favoritada: false
        }),
        watch:{
          favoritada(valorNovo){
            if(valorNovo){
              this.emitter.emit('favoritarVaga', this.titulo)
            }else{
              this.emitter.emit('desfavoritarVaga', this.titulo)
            }
          }
        },
        //props:['titulo', 'descricao', 'salario', 'modalidade', 'tipo', 'publicacao']
        props: {
          titulo:{
            type: String,
            required: true,
            validador(t){
              //console.log('Prog: ', p)
              if(t.lenght < 100) return false
              return true
            }
          },
          descricao:{
            type: String,
            default: 'O contratante não colocou descrição a vaga'
          },
          salario:{
            type: [Number, String],
            required: true
          },
          modalidade:{
            type: String,
            required: true
          },
          tipo:{
            type: String,
            required: true
          },
          publicacao:{
            type: String,
            required: true
          }          
        },
        computed:{
          getmodalidade(){
            switch (this.modalidade) {
              case '1' : return 'Home Oficce'
              
              case '2' : return 'Presencial'

              default:
                break;
            }
            return ''
          },
          gettipo(){
            switch (this.tipo) {
              case '1' : return 'CLT'
              
              case '2' : return 'PJ'

              default:
                break;
            }
            return ''
          },
          getpublicacao(){
            let dataPublicacao = new Date(this.publicacao)
            return dataPublicacao.toLocaleDateString('pt-br')
          }
        },
        methods: {

        },
    }
</script>