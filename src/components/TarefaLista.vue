<template>
    <BoxContainer>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div>
                <CronometroDisplay :tempoEmSegundo="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxContainer>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroDisplay from './CronometroDisplay.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxContainer from './BoxContainer.vue';

export default defineComponent({
    name: 'TarefaLista',
    components: {
        CronometroDisplay,
        BoxContainer
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>

