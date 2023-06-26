<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                Descrição da tarefa
            </div>
            <div>
                <CronometroDisplay :tempoEmSegundo="15"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroDisplay from './CronometroDisplay.vue';

export default defineComponent({
    name: 'TarefaLista',
    components: {
        CronometroDisplay
    }
})
</script>

<style scoped>
.box {
    background: #FAF0CA;
}
</style>