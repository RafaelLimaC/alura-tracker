<template>
    <div class="box formulario">
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
    emits: ['aoSalvarTarefa'],
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
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricaoTarefa
            })
            this.descricaoTarefa = ''
        }
    }
})
</script>

<style>
.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
}
</style>
