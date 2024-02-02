<template>
<button class="button" @click="clicado" :disabled="desabilitado">
        <span class="icon">
            <i :class="Icone"   ></i>
        </span>
        <span>{{nomeBotao}}</span>
        </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name:"BotaoA",
    emits:['clicado'],
    props:{
        desabilitado:{
            type: Boolean
        },
        nomeBotao:{
            type: String
        },
        Icone:{
            type: String
        }
    },
    methods:{
        clicado ():void{
            this.$emit("clicado")
        }
    }
})
</script>