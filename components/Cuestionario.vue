<template>
  <div class="quiz">
    <Cuestionario
      v-for="(pregunta, index) in preguntas"
      :key="index"
      :pregunta="pregunta.pregunta"
      :opciones="pregunta.opciones"
      @respuesta="guardarRespuesta(index, $event)"
    />
    <button @click="calificar">Calificar</button>
  </div>
</template>

<script>
import Cuestionario from '~/components/Cuestionario.vue'

export default {
  components: {
    Cuestionario
  },
  data() {
    return {

      respuestas: []
    }
  },
  methods: {
    guardarRespuesta(index, respuesta) {
      this.$set(this.respuestas, index, respuesta)
    },
    calificar() {
      let aciertos = 0
      this.respuestas.forEach((respuesta, index) => {
        if (respuesta === preguntas[index].respuestaCorrecta) {
          aciertos++
        }
      })
      alert(`Calificación: ${aciertos}/${preguntas.length}`)
    }
  },
}
</script>

