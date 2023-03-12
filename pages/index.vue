<template>
  <div style="display: flex; justify-content: center">
  <div style="width: 900px; margin-top: 20px">
    <h1>CUESTIONARIO SISTEMAS INFORMACION</h1>
    <div v-for="(pregunta, index) in preguntas" :key="index">
      <h3>{{ pregunta.pregunta }}</h3>
      <ul>
        <li v-for="(opcion, i) in pregunta.opciones" :key="i">
          <input type="radio" :id="`pregunta-${index}-opcion-${i}`" :name="`pregunta-${index}`" :value="i" v-model="respuestas[index]">
          <label :for="`pregunta-${index}-opcion-${i}`">{{ opcion }}</label>
        </li>
      </ul>
    </div>
    <button @click="calificar">Enviar respuestas</button>
    <div v-if="calificado">
      <h2>Calificación: {{ calificacion }}/{{ preguntas.length }}</h2>
      <ul>
        <li v-for="(pregunta, index) in preguntas" :key="index" :class="{'respuesta-correcta': respuestaCorrecta(pregunta, respuestas[index]), 'respuesta-incorrecta': !respuestaCorrecta(pregunta, respuestas[index])}">
          <h3>{{ pregunta.pregunta }}</h3>
          <ul>
            <li v-for="(opcion, i) in pregunta.opciones" :key="i">
              <input type="radio" :id="`pregunta-${index}-opcion-${i}`" :name="`pregunta-${index}`" :value="i" :disabled="true" :checked="i === respuestas[index]">
              <label :for="`pregunta-${index}-opcion-${i}`" :style="{color: respuestaCorrecta(pregunta, i) ? 'green' : 'red'}">{{ opcion }}</label>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      preguntas: [
        {
          pregunta: "Una de las variantes en las que se interpreta La ley de Moore nos dice:",
          opciones: [
            "El poder de computo se duplica cada 18 meses",
            "El poder de almacenamiento se duplica cada 18 meses",
            "El poder de memoria se duplica cada 18 meses",
            "El poder comunicación se duplica cada 18 meses"
          ],
          respuestaCorrecta: 0
        },
        {
          pregunta: "La consumerización de TI y BYOD se le entiende como:",
          opciones: [
            "Implica que los dispositivos móviles son el medio básico para el acceso a internet",
            "La tecnología emergente primero llega al mercado de consumidor y luego se extiende a los negocios",
            "En donde los dispositivos werable se adhieren a la plataforma digital móvil",
            "En la que el poder de procesamiento permite resolver problemas complejos"
          ],
          respuestaCorrecta: 1
        },
        {
          pregunta: "En los SI gerencial hay algunos cambios interrelacionados, uno de ellos es:",
          opciones: [
            "La adopción de base de datos con  formatos no estructurados",
            "El crecimiento de la infraestructura y líneas de comunicación",
            "La robotización como un fenómeno de cambio en el aspecto laboral",
            "La computación en la nube para software de negocio"
          ],
          respuestaCorrecta: 3
        },
        {
          pregunta: "Según lo estudiado en clase, las empresas usan la tecnología de la información para responder con rapidez varios elementos de negocios, Excepto:",
          opciones: [
            "Los cambios en la demanda y preferencia del mercado",
            "Lograr mayor eficiencia operacional",
            "Reducir los inventarios a los niveles óptimos posibles",
            "Controlar el uso de redes sociales para enfocarse en los objetivos estratégicos"
          ],
          respuestaCorrecta: 3
        },
        {
          pregunta: "En los impactos de los SI en las empresas han sido profundo y transversales. Desde el punto de vista económico tenemos:",
          opciones: [
            "Las empresas pueden desplazar el conocimiento de sus trabajadores más rápidamente.",
            "Facilita el aplanamiento de jerarquías",
            "Generan riesgos asociados a la resistencia del cambio",
            "Pueden llevar a un “adelgazamiento” de la empresa sin perder ingresos"
          ],
          respuestaCorrecta: 3
        },
        {
          pregunta: "En estos últimos años se han desarrollado varias formas de modelos de negocio, ingresos y tipos de e-commerce. En cuanto al primero (modelo de negocio), aquel relacionado con la distribución de información digital en línea a precios accesibles y de fácil reproducción en varios dispositivos se relaciona con:",
          opciones: [
            "Creador de mercado",
            "E-Tailer",
            "Proveedor de contenido",
            "Proveedor de servicios"
          ],
          respuestaCorrecta: 2
        },
        {
          pregunta: "El ERP nos ayuda a responder ciertas preguntas universales de la producción. Seleccione cual de ellas no es la correcta",
          opciones: [
            "Que es lo que tengo de material",
            "Donde voy a vender el producto",
            "Cuanto tiempo toma fabricar",
            "Que necesito producir"
          ],
          respuestaCorrecta: 1
        },
      ],

      respuestas: [],
      calificado: false
    }
  },
  methods: {
    calificar() {
      // Calcular la calificación
      const numCorrectas = this.preguntas.reduce((total, pregunta, index) => {
        if (this.respuestas[index] === pregunta.respuestaCorrecta) {
          return total + 1
        } else {
          return total
        }
      }, 0)
      this.calificado = true
      this.calificacion = numCorrectas
    },
    respuestaCorrecta(pregunta, opcionSeleccionada) {
      return pregunta.respuestaCorrecta === opcionSeleccionada
    }
  }
}
</script>

<style scoped>
.respuesta-correcta {
  border: 2px solid green;
  padding: 10px;
  margin-bottom: 10px;
}
.respuesta-incorrecta {
  border: 2px solid red;
  padding: 10px;
  margin-bottom: 10px;
}
</style>

