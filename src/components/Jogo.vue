<template>
  <div class="jogo">
    <Forca
    :erros="erros"
    />
    <Palavra
    :palavra="palavra"
    :dica="dica"
    :verificarLetra="verificarLetra"
    :etapa="etapa"
    />
    <Teclado
    v-if="etapa === 'jogo'"
    :letras="letras"
    :verificarLetra="verificarLetra"
    :jogar="jogar"
    />
    <Final
    v-if="etapa != 'jogo'"
    :etapa="etapa"
    :texto="etapa === 'ganhador' ? 'Parabéns =]' : 'Game Over =['"
    :jogarNovamente="jogarNovamente"
    />
  </div>
</template>
<script>
import Forca from './Forca.vue'
import Palavra from './Palavra.vue'
import Teclado from './Teclado.vue'
import Final from './Final.vue'
export default {
    // eslint-disable-next-line 
    name: 'Jogo',
    components:{
        Forca,
        Palavra,
        Teclado,
        Final,
        
    },
    props:{
    
        erros: Number,
        palavra: String,
        dica: String,
        verificarLetra: Function,
        jogar: Function,
        jogarNovamente: Function,
        etapa: String,
        letras: Array
     
    },
    data(){
        return{
            

        }

    },
    methods: {

    }


}
</script>

<style>
   .jogo{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
   }
</style>