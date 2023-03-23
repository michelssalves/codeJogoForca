<template>
  <div id="app">
    <h1>Jogo da Forca</h1>
    <section v-if="tela === 'inicio'" id="inicio">
      <Formulario
      v-if="etapa === 'palavra'"
      title="Defina a Palavra"
      button="Next"
      :action="setPalavra"
      />
      <Formulario
      v-if="etapa === 'dica'"
      title="Defina a Dica"
      button="Start"
      :action="setDica"
      />
    </section>
    <section v-if="tela === 'jogo'" id="jogo">
      <Jogo
      :erros="erros"
      :palavra="palavra"
      :dica="dica"
      :verificarLetra="verificarLetra"
      :jogar="jogar"
      :etapa="etapa"
      :letras="letras"
      :jogarNovamente="jogarNovamente"
      />
   
    </section>
  </div>
</template>
<script>
import '@/assets/css/global.css';
import Formulario from '@/components/Formulario';
import Jogo from '@/components/Jogo';
  export default{
    name: 'App',
    components:{
      Formulario,
      Jogo
    },
    data(){
      return{
        tela: 'inicio',
        etapa:'palavra',
        palavra: '',
        dica: '',
        erros: 0,
        letras: [],

      }
    },
    methods:{
        setPalavra: function(palavra){
          this.palavra = palavra
          this.etapa = 'dica'
        },
        setDica: function(dica){
          this.dica = dica
          this.tela = 'jogo'
          this.etapa = 'jogo'
        },
        verificarLetra: function(letra){
          return this.letras.find(item => item.toLowerCase() === letra.toLowerCase())
        },
        jogar: function(letra){

          this.letras.push(letra)
          this.verificarErros(letra)
        },
        verificarErros: function(letra){
          if(this.palavra.toLocaleLowerCase().indexOf(letra.toLocaleLowerCase()) >= 0){
              return this.verificarAcertos()
          }

          this.erros++

          if(this.erros === 6){
            this.etapa = 'enforcado'
          }
        },
        verificarAcertos: function(){
          let letrasUnicas = [...new Set(this.palavra.split(''))]
          if(letrasUnicas.length === (this.letras.length - this.erros)){
            this.etapa = 'ganhador'
          }
        },
        jogarNovamente: function(){

           this.palavra = ''
           this.dica = ''
           this.erros = 0
           this.letras = []
           this.tela = 'inicio'
           this.etapa = 'palavra'

        }
    },


  }
</script>
<style>
#app{
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
