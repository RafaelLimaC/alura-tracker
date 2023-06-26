<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja inciar?" v-model="descricaoTarefa">
            </div>
            <div class="column">
                <TemporizadorCronometro @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorCronometro from './TemporizadorCronometro.vue'

export default defineComponent({
    nome: 'FormularioTarefa',
    components: {
        TemporizadorCronometro
    },
    data () {
        return {
            descricaoTarefa: ''
        }
    },
    methods: {
        finalizarTarefa (tempoDecorrido: number) : void {
            console.log("Tempo da tarefa: ", tempoDecorrido)
            console.log("Descrição da tarefa: ", this.descricaoTarefa)
            this.descricaoTarefa = ''
        }
    }
})
</script>
