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
          pregunta: "Los sistemas empresariales generan valor al negocio como los que se indica en la lista EXCEPTO:",
          opciones: [
            "Permiten evaluar el desempeño organizacional",
            "Utilizan información para crear pronósticos mas precisos de venta y producción",
            "Estandarizan las prácticas de negocio y los datos",
            "Posibilitan el mayor rendimiento de los activos de infraestructura"
          ],
          respuestaCorrecta: 3
        },
        {
          pregunta: "El ERP nos ayuda a responder ciertas preguntas universales de la producción. Seleccione cual de ellas no es la correcta",
          opciones: [
            "Que es lo que tengo de material",
            "Donde voy a vender el producto",
            "Cuanto tiempo toma fabricar",
            "Que necesito producir",
          ],
          respuestaCorrecta: 1
        },
        {
          pregunta: "El tipo de software de cadena de suministro que ayuda a gestionar los pasos de la cadena se denomina",
          opciones: [
            "SCM de planeación",
            "SCM de automatización",
            "SCM de ejecución",
            "SCM de operación"
          ],
          respuestaCorrecta: 2
        },
        {
          pregunta: "Los sistemas de planificación de recursos empresariales ERP usualmente recogen una gran cantidad de datos de las áreas de la empresa para",
          opciones: [
            "Disponerlos en módulos para establecer las interfaces necesarias con el resto de sistemas",
            "Ponerlos a disposición de las aplicaciones que soportan las actividades de negocio internas",
            "Extender la relación entre ellos y permitir su explotación analítica",
            "Dar soporte a las aplicaciones que soportan la oferta y la demanda externa",
          ],
          respuestaCorrecta: 1
        },
        {
          pregunta: "Entre los conceptos asociados a la cadena de suministro tenemos",
          opciones: [
            "Permitir convertir este flujo en un proceso eficiente enfocado en la satisfacción del cliente",
            "Son sistemas que permiten una toma de decisiones mas efectiva sobre todo en el nivel gerencial",
            "Permite recolectar información de varios departamentos y ponerlos a disposición de los procesos de negocio",
            "Son sistemas flexibles que permiten adaptar con rapidez la forma de trabajar y los procesos de negocio"
          ],
          respuestaCorrecta: 0
        },
        {
          pregunta: "Uno de los efectos nocivos en una mala cadena de suministro es el efecto látigo. Este fenómeno se refiere a",
          opciones: [
            "La información de la demanda de un producto se distorsiona cuando viaja del consumidor hasta llegar al proveedor fabricante",
            "La información de la demanda de un producto se distorsiona cuando el fabricante no conoce los planes de aprovisionamiento del proveedor",
            "La información de la demanda de un producto se distorsiona cuando viaja desde el productor hacia el distribuidor y luego el cliente",
            "La información de la demanda de un producto se distorsiona cuando la demanda tiene altos niveles de variabilidad"
          ],
          respuestaCorrecta: 0
        },
        {
          pregunta: "El software de cadena de suministro que permite la planificación de la cadena permite a la organización:",
          opciones: [
            "Administrar eficazmente el flujo de productos en el entorno",
            "Mejorar la administración de materiales y las operaciones logísticas",
            "Generar pronósticos de abastecimiento más precisos",
            "Generar pronósticos de la demanda óptimos"
          ],
          respuestaCorrecta: 3
        },
        {
          pregunta: "Una deficiencia en las organizaciones es gestionar inadecuadamente la reserva de seguridad. Según la definición correcta, ésta actúa como",
          opciones: [
            "Un almacén de reserva para gestionar los materiales críticos para la producción",
            "Un almacén de reserva para compensar la falta de flexibilidad de la cadena",
            "Un almacén dinámico para flujos de entrada y salida de productos",
            "Un almacén virtual para satisfacer los pedidos de clientes"
          ],
          respuestaCorrecta: 1
        },
        {
          pregunta: "El ERP puede atacar varios problemas en una empresa, sin embargo de los discutidos en clase seleccione cual seria la mejor aproximación",
          opciones: [
            "Gestión no transaccional con los clientes",
            "Control de inventarios y flujo de caja",
            "Abastecimiento en la cadena de distribución",
            "Automatización del flujo de trabajo"
          ],
          respuestaCorrecta: 3
        },
        {
          pregunta: "Las compañías deberían aprovechar al máximo los beneficios que trae el software empresarial ERP para ello se aconseja",
          opciones: [
            "Adaptar los procesos del ERP a través de personalizaciones que se ajusten a las necesidades",
            "Durante la implementación se puede re-escribir para del software para apoyar sus procesos de negocio",
            "Evaluar sus prácticas de negocio versus estándares reconocidos como por ejemplo las normas ISO",
            "Adaptar su forma de trabajo a los procesos de negocios definidos en el software"
          ],
          respuestaCorrecta: 3
        },
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
        },
        {
          pregunta: "La plataforma como servicio PAAS se entiende como aquella forma de infraestructura en la nube que:",
          opciones: [
            "Sirve para desarrollar aplicaciones a través de herramientas de programación hospedadas",
            "Usan recursos de computo como procesamiento y almacenamiento para operar sus sistemas informáticos",
            "Utilizan prácticas y tecnologías que minimizan el impacto sobre el entorno"
          ],
          respuestaCorrecta: 0,
        },
        {
          pregunta: "La infraestructura como servicio IaaS se entiende como aquella forma de infraestructura en la nube que:",
          opciones: [
            "Sirve para desarrollar aplicaciones a través de herramientas de programación hospedadas",
            "Usan recursos de computo como procesamiento y almacenamiento para operar sus sistemas informáticos",
            "Utilizan prácticas y tecnologías que minimizan el impacto sobre el entorno"
          ],
          respuestaCorrecta: 1,
        },
        {
          pregunta: "La plataforma como servicio PAAS se entiende como aquella forma de infraestructura en la nube que:",
          opciones: [
            "Sirve para desarrollar aplicaciones a través de herramientas de programación hospedadas",
            "Usan recursos de computo como procesamiento y almacenamiento para operar sus sistemas informáticos",
            "Utilizan prácticas y tecnologías que minimizan el impacto sobre el entorno"
          ],
          respuestaCorrecta: 2,
        },
        {
          pregunta: "La infraestructura como servicio IaaS se entiende como aquella forma de infraestructura en la nube que:",
          opciones: [
            "Sirve para desarrollar aplicaciones a través de herramientas de programación hospedadas",
            "Usan recursos de computo como procesamiento y almacenamiento para operar sus sistemas informáticos",
            "Utilizan prácticas y tecnologías que minimizan el impacto sobre el entorno"
          ],
          respuestaCorrecta: 1,
        },
        {
          pregunta: "La plataforma como servicio PAAS se entiende como aquella forma de infraestructura en la nube que:",
          opciones: [
            "Sirve para desarrollar aplicaciones a través de herramientas de programación hospedadas",
            "Usan recursos de computo como procesamiento y almacenamiento para operar sus sistemas informáticos",
            "Utilizan prácticas y tecnologías que minimizan el impacto sobre el entorno"
          ],
          respuestaCorrecta: 0,
        },
        {
          pregunta: "¿Qué beneficios ofrece la plataforma como servicio (PaaS) en la nube?",
          opciones: [
            "Permite almacenar grandes cantidades de información de manera eficiente.",
              "Ofrece soluciones de seguridad avanzadas para proteger los datos de los usuarios.",
              "Facilita el desarrollo de aplicaciones a través de herramientas de programación hospedadas.",
            "Sirve para desarrollar aplicaciones a través de herramientas de programación\n" +
            "hospedadas."
          ],
          respuestaCorrecta: 3,
        },
          {
            pregunta: "Que es el comercio electrónico:",
            opciones: [
              "Gestionar la relación con los consumidores de servicios.",
              "Son transacciones comerciales con capacidad digital entre organizaciones e individuos.",
              "Alinea los servicios ofrecidos de los que depende la organización.",
              "Sirve de guía a la hora de establecer y priorizar objetivos"
            ],
            respuestaCorrecta: 1
          },
          {
            pregunta: "Características de la tecnología del comercio electrónico:",
            opciones: [
              "Gestión de cambios, estrategia, diseño, planeación, entregables, despliegues.",
              "Planificación de la evaluación, estrategia, diseño, planeación, Enfoques Técnicos.",
              "Estrategia, diseño, planeación, enfoques técnicos, planeación, entregables, despliegues.",
              "Ubicuidad, Alcance Global, Estándares Universales, Riqueza, Interactividad, Densidad de la información"
            ],
            respuestaCorrecta: 3
          },
          {
            pregunta: "Tipos de Comercio electrónico:",
            opciones: [
              "Negocio a consumidor(B2C), Negocio a negocio(B2B), Consumidor a consumidor(C2C).",
              "Negocio a producto(B2P), Negocio a consumidor(B2C), Bodega a consumidor(C2C).",
              "Producto a consumidor(P2C), Bodega a negocio(B2B), Bodega a consumidor(C2C).",
              "Casa a consumidor(B2C), Negocio a negocio(B2B), Comercio a consumidor(C2C)"
            ],
            respuestaCorrecta: 0
          },
          {
            pregunta: "¿Cuál de las siguientes no es una característica del comercio electrónico móvil (mcommerce) ?:",
            opciones: [
              "Capacidad multimedia limitada.",
              "Publicidad inalámbrica.",
              "Checar el presupuesto para equipo de toda la empresa.",
              "Acceso a servicios de comercio en cualquier lugar."
            ],
            respuestaCorrecta: 2
          },
          {
            pregunta: "Pasos para la creación de un sitio web de comercio electrónico:",
            opciones: [
              "Decisión de crear, presupuesto, construcción, hospedaje, publicidad, mantenimiento.",
              "Definir el estado del objetivo, plan del programa, publicidad, mantenimiento.",
              "Declaración de acciones, establecer principios y políticas, ejecutar estrategia",
              "Requisitos de cumplimiento, acceso a las redes sociales, mantenimiento."
            ],
            respuestaCorrecta: 0
          },
        {
          pregunta: "Las divisas virtuales son tecnologías disruptivas que ofrecen algunas ventajas, tales como:",
          opciones: [
            "Proveen confianza entre los actores",
            "Promueven la centralización de las estructuras económicas",
            "Garantizan la transacción",
            "Tienen costos de transacción"
          ],
          respuestaCorrecta: 0
        },
        {
          pregunta: "Los métodos de consenso son claves en el funcionamiento de una cadena de bloques. Cuál de las siguientes opciones es una función clave de los métodos de consenso?",
          opciones: [
            "Garantiza que al menos 1 minero honesto produce una salida válida",
            "Permite confirmar la validez de la petición de transacción",
            "Garantiza la integridad de la cadena",
            "Es resistente a errores que surjan en la red o en el conjunto de nodos"
          ],
          respuestaCorrecta: 3
        }
      ],
      respuestas: [],
      calificado: false
    }
  },
  mounted() {
    this.preguntas = this.preguntas.sort(this.aleatorio)
  },
  methods: {
    aleatorio() {
  return Math.random() - 0.5;
},
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

