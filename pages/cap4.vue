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
          pregunta: "En la actualidad los productos o servicios tienen ciclos de vida que se caracterizan por",
          opciones: [
            "Ser innovadores y tener ciclos de vida cortos",
            "El impulso que dan las marcas en diferentes ámbitos como la redes sociales",
            "Ser innovadores y generar tendencias que persistan en el tiempo",
            "Tener una alta variabilidad en la demanda"
          ],
          respuestaCorrecta: 0,
        },
        {
          pregunta: "En estos últimos años se han desarrollado varias formas de modelos de negocio\
  ingresos y tipos de e-commerce. En cuanto al primero (modelo de negocio), aquel\
  relacionado con la distribución de información digital en línea a precios accesibles y\
  de fácil reproducción en varios dispositivos se relaciona con",
          opciones: [
            "Creador de mercado",
            "E-Tailer",
            "Proveedor de contenido",
            "Proveedor de servicios"
          ],
          respuestaCorrecta: 2,
        },
        {
          pregunta: "Hay elementos claves para entender el nuevo panorama de e-commerce, estos se\
  relacionan con",
          opciones: [
            "La adaptación, lo social y lo móvil",
            "Lo social, lo móvil y la ubicación",
            "La demanda y el abastecimiento",
            "Lo social, lo oblicuo y la interactividad"
          ],
          respuestaCorrecta: 1,
        },
        {
          pregunta: "Según lo estudiado en clase, las empresas usan la tecnología de la información para\
  responder con rapidez varios elementos de negocios, Excepto",
          opciones: [
            "Los cambios en la demanda y preferencia del mercado",
            "Lograr mayor eficiencia operacional",
            "Reducir los inventarios a los niveles óptimos posibles",
            "Controlar el uso de redes sociales para enfocarse en los objetivos estratégicos"
          ],
          respuestaCorrecta: 3,
        },
        {
          pregunta: "¿Los sistemas de administración de las relaciones con el cliente nos dice que?",
          opciones: [
            "Su principal objetivo es automatizar sus servicios y tener su información en un solo\
            lugar, esto se logra gracias al uso de sistemas empresariales como lo es un ERP.\
            También mejorar su toma de decisiones para darle valor competitivo a la empresa.",
            "Aportan información para coordinar todos los procesos de negocios relacionados con\
            los clientes en las áreas de ventas, marketing y servicio al cliente, para optimizar los\
            ingresos, al igual que la satisfacción y la retención del cliente"
          ],
          respuestaCorrecta: 1,
        },
        {
          pregunta: "Describa un objetivo específico por lo que las empresas inviernen en un sistema de información",
          opciones: [
            "Su principal objetivo es automatizar sus servicios y tener su información en un solo\
            lugar, esto se logra gracias al uso de sistemas empresariales como lo es un ERP.\
            También mejorar su toma de decisiones para darle valor competitivo a la empresa.",
            "Aportan información para coordinar todos los procesos de negocios relacionados con\
            los clientes en las áreas de ventas, marketing y servicio al cliente, para optimizar los\
            ingresos, al igual que la satisfacción y la retención del cliente"
          ],
          respuestaCorrecta: 0,
        }
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

