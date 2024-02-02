<template>
    <div 
        class="is-flex is-align is-align-items-center is-justify-content-space-between">

        <Cronometro :tempoEmSegundos="tempoEmSegundos"/>

        <Botao @clicado="iniciar" :nomeBotao="'Play'"  :Icone="'fas fa-play'" :desabilitado="cronometroRodando" />
        <Botao @clicado="finalizar" :nomeBotao="'Stop'"  :Icone="'fas fa-stop'" :desabilitado="!cronometroRodando" />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Cronometro from "./Cronometro.vue"
import Botao from './Botao.vue'

export default defineComponent({
    name:"TemporizadorA",
    emits:['aoTemporizadorFinalizado'],
    components: {
        Cronometro,
        Botao
    },
    data(){
        return{
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods:{
        
        iniciar(){
            //começar a contagem
            this.cronometro = setInterval(()=>{
                this.tempoEmSegundos++
            }, 1000)
            this.cronometroRodando = true
            console.log("Iniciando");
        },
        finalizar() {
            //finalizar a contagem
            clearInterval(this.cronometro)
            this.cronometroRodando = false
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0;
            console.log("Finalizando");
        }
    }
})
</script>