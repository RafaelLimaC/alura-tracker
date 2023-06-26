<template>
    <secton>
        <strong>
            {{ tempoDecorrido }}
        </strong>
    </secton>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'CronometroDisplay',
    props: {
        tempoEmSegundo: {
            type: Number,
            default: 0
        }
    },
    computed: {
        tempoDecorrido () : string {
            return new Date(this.tempoEmSegundo * 1000).toISOString().substring(11, 19)
        }
    }
})
</script>