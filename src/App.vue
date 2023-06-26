<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTarefa @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaLista v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxContainer v-if="listaEstaVazia">
          Você não está muito produtivo hoje :c
        </BoxContainer>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import FormularioTarefa from './components/FormularioTarefa.vue'
import TarefaLista from './components/TarefaLista.vue'
import ITarefa from './interfaces/ITarefa'
import BoxContainer from './components/BoxContainer.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTarefa,
    TarefaLista,
    BoxContainer
  },
  data () {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema (modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primario: #FFFFFF;
  --texto-primario: #000000
}
main.modo-escuro {
  --bg-primario: #2d2d42;
  --texto-primario: #ddd
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
