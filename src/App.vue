<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <Formulario @aoSalvarTarefa="salvarTarefa" />
      <!-- Lista de Tarefas  -->
      <div class="lista">
        <ListaTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <Box v-if="listaEstaVazia">
          Você não está muito produtivo hoje :(
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import BarraLateral from "./components/BarraLateral.vue"
import Formulario from "./components/FormularioPrinicipal.vue"
import ListaTarefa from "./components/ListaTarefa.vue"
import ITarefa from './interfaces/ITarefa'
import Box from './components/Box.vue'

export default defineComponent({
  name: "App",
  components: { BarraLateral, Formulario, ListaTarefa, Box },
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    listaEstaVazia () : boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
      console.log(tarefa)
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
</style>
