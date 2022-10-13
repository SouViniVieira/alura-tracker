<template>
  <section class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <BotaoTemp @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
    <BotaoTemp @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";
import BotaoTemp from "./BotaoTemp.vue";

export default defineComponent({
  name: "TemporiZador",
  emits: ['aoTemporizadorFinalizado'],
  components: {
    Cronometro,
    BotaoTemp
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false,
    };
  },
  methods: {
    iniciar() {
      //Começar a contagem
      //1 seg = 1000 ms
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1
      }, 1000);
    },
    finalizar() {
      this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
    },
  },
});
</script>
