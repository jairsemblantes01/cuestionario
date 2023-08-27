<template>
  <div style="display: flex; justify-content: center">
  <div style="width: 900px; margin-top: 20px">
    <h1>CUESTIONARIO GESTION PROYECTOS</h1>
    <div v-for="(pregunta, index) in preguntas" :key="cuestionarioinformatica">
      <h3>{{ pregunta.pregunta }}</h3>
      <ul>
        <li v-for="(opcion, i) in pregunta.opciones" :key="i">
          <input type="radio" :id="`pregunta-${cuestionarioinformatica}-opcion-${i}`" :name="`pregunta-${cuestionarioinformatica}`" :value="i" v-model="respuestas[cuestionarioinformatica]">
          <label :for="`pregunta-${cuestionarioinformatica}-opcion-${i}`">{{ opcion }}</label>
        </li>
      </ul>
    </div>
    <button @click="calificar">Enviar respuestas</button>
    <div v-if="calificado">
      <h2>Calificación: {{ calificacion }}/{{ preguntas.length }}</h2>
      <ul>
        <li v-for="(pregunta, index) in preguntas" :key="cuestionarioinformatica" :class="{'respuesta-correcta': respuestaCorrecta(pregunta, respuestas[cuestionarioinformatica]), 'respuesta-incorrecta': !respuestaCorrecta(pregunta, respuestas[cuestionarioinformatica])}">
          <h3>{{ pregunta.pregunta }}</h3>
          <ul>
            <li v-for="(opcion, i) in pregunta.opciones" :key="i">
              <input type="radio" :id="`pregunta-${cuestionarioinformatica}-opcion-${i}`" :name="`pregunta-${cuestionarioinformatica}`" :value="i" :disabled="true" :checked="i === respuestas[cuestionarioinformatica]">
              <label :for="`pregunta-${cuestionarioinformatica}-opcion-${i}`" :style="{color: respuestaCorrecta(pregunta, i) ? 'green' : 'red'}">{{ opcion }}</label>
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
          "pregunta": "La estructura conceptual del PMBok contiene lo siguiente",
          "opciones": [
            "Grupo de procesos, normas técnicas, áreas de conocimiento",
            "Grupos de procesos, áreas de conocimiento, gestión de stakeholders",
            "Definición del ciclo de vida, grupos de proceso, áreas de conocimiento",
            "Definición del ciclo de vida, normas técnicas, grupos de procesos"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "La última versión de la estándar de PMBok Guide tiene la siguiente característica.",
          "opciones": [
            "Es la versión número 6 y esta totalmente alineada con la norma ISO 9000",
            "Es la versión número 5 y esta totalmente alineada con la norma ISO 9000",
            "Es la versión número 6 y esta totalmente alineada con la norma ISO 21500",
            "Es la versión número 5 y esta totalmente alineada con la norma ISO 21500"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Los grupos de procesos propuestos por el PMBOK son:",
          "opciones": [
            "Inicio, ejecución, cierre",
            "Identificación, selección, priorización, ejecución y cierre",
            "Inicio, planificación, ejecución, monitoreo y control, cierre",
            "Identificación, selección, planificación, ejecución, cierre"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Un ciclo de vida adaptativo procura:",
          "opciones": [
            "Generar ciclos iterativos de planificación bajo elaboración progresiva de requisitos",
            "Desarrollar planes evolutivos y graduales de adaptación ágil",
            "Generar planes consolidados para mejorar la gestión del riesgo",
            "Generar planes detallado en todas las fases para adaptarse a los requisitos"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Según lo visto en clase, el PMI asocia la definición de un proyecto como:",
          "opciones": [
            "El conjunto de actividades de una cadena crítica orientados a un objetivo específico",
            "Al trabajo que realiza una organización para dirigirse a una situación deseada",
            "Aquella combinación de recursos de una organización establecidos para conseguir un propósito",
            "Aquel esfuerzo temporal emprendido para crear un servicio único"
          ],
          "respuestaCorrecta": 3
        },
        {
          "pregunta": "Los grupos de procesos propuestos por el PMBOK son:",
          "opciones": [
            "Inicio, ejecución, cierre",
            "Identificación, selección, priorización, ejecución y cierre",
            "Inicio, planificación, ejecución, monitoreo y control, cierre",
            "Identificación, selección, planificación, ejecución, cierre"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Un ciclo adaptativo procura",
          "opciones": [
            "Generar ciclos iterativos de planificación bajo elaboración progresiva de requisitos",
            "Desarrollar planes evolutivos y graduales para adaptación ágil",
            "Generar planes consolidados para mejorar la gestión del riesgo",
            "Generar planes detallado en todas las fases para adaptarse a los requisitos"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Si usted fuera el director general de una empresa desarrolladora de software que tipo de organización escogería:",
          "opciones": [
            "De tipo proyectizada",
            "De tipo matricial débil",
            "De tipo Project coordinator",
            "De tipo Project expeditor"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Un director de proyectos tiene muy poca experiencia en proyectos, pero ha sido asignado como director de un nuevo proyecto. Dado que estará trabajando en una organización matricilal para completar su proyecto, puede esperar que las comunicaciones resulten",
          "opciones": [
            "Simples",
            "Abiertas y precisas",
            "Complejas",
            "Difíciles de automatizar"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Los pasos para definir el cronograma del proyecto son los siguientes:",
          "opciones": [
            "Definir listados entregables, secuenciar actividades, estimar recursos y elaborar cronograma",
            "Definir listado actividades, secuenciar actividades, estimar recursos, definir duración actividades, elaborar cronograma",
            "Definir listado de actividades, definir duración de actividades, elaborar cronograma",
            "Definir paquete de trabajo, definir listado de actividades, definir duración de actividades, elaborar cronograma"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "Un índice de desempeño del costo CPI de 0.89 significa:",
          "opciones": [
            "En este momento esperamos que el proyecto total cueste 89% mas de lo planificado",
            "Una vez completado el proyecto habremos gastado el 89% mas de lo planificado",
            "El proyecto progresa a 89% del ritmo previsto",
            "El proyecto está obteniendo 89 ctvs de cada dólar invertido"
          ],
          "respuestaCorrecta": 1
        },
          {
            "pregunta": "El acta de constitución es un documento formal que reconoce la existencia del proyecto. Este documento confiere las siguientes atribuciones",
            "opciones": [
              "Permite al sponsor autorizar el plan de dirección del proyecto",
              "Confiere al director de proyecto la administración del presupuesto y la reserva de la gestión",
              "Permite al comité directivo iniciar el proyecto en base al plan de requisitos documentados",
              "Confiere al director de proyecto la autoridad para asignar los recursos de la organización al proyecto"
            ],
            "respuestaCorrecta": 3
          },
            {
              "pregunta": "El juicio de expertos es un _ del proceso de definición del alcance",
              "opciones": [
                "Entrada",
                "Herramienta/técnica",
                "Salida",
                "Entrada y salida"
              ],
              "respuestaCorrecta": 1
            },
            {
              "pregunta": "Durante una reunión del equipo del proyecto, un miembro del equipo sugiere una mejora para el alcance que va más allá del alcance del acta constitucional del proyecto. El director del proyecto señala que el equipo necesita concentrarse en finalizar todo el trabajo y solo el trabajo solicitado. Esto es un ejemplo de",
              "opciones": [
                "Proceso de la gestión de cambios",
                "Gestión del alcance",
                "Análisis de calidad",
                "Desglose del alcance"
              ],
              "respuestaCorrecta": 1
            },
            {
              "pregunta": "La evaluación, estructuración y formulación de un proyecto, es desde todo punto de vista:",
              "opciones": [
                "Una metodología",
                "Una buena práctica",
                "Un modo de no perderse en la cantidad de tópicos de cada proyecto",
                "Ninguna"
              ],
              "respuestaCorrecta": 0
            },
            {
              "pregunta": "Cuáles son las disciplinas o áreas de conocimiento fundamentales que debe enfrentar ante la estructuración de un proyecto en su concepción:",
              "opciones": [
                "Costos, tiempo, alcance",
                "Personas, procesos, tecnología",
                "Riesgos, contratos, comunicación",
                "Finanzas, calidad, integración"
              ],
              "respuestaCorrecta": 0
            },
            {
              "pregunta": "Realizar un análisis amplio de los resultados financieros, económicos y sociales de inversión en un proyecto se dice de:",
              "opciones": [
                "Estudio de factibilidad",
                "Estudio económico",
                "Estudio métricas",
                "Ninguno"
              ],
              "respuestaCorrecta": 0
            },
            {
              "pregunta": "¿Qué entiende por planificar un proyecto usando PMBOK?",
              "opciones": [
                "Construir un cronograma",
                "Construir una lista de experiencias de usuario",
                "Llevar el control de los gastos las personas los recursos operativos entre otros",
                "Construir un set de planes que focalicen procesos de especialización en áreas de conocimiento específico",
                "Ninguna de las anteriores"
              ],
              "respuestaCorrecta": 3
            },
            {
              "pregunta": "Algunas áreas de conocimiento propuestas por el PMBok son:",
              "opciones": [
                "Gestión del plan estratégico, gestión de indicadores, Gestión de adquisición.",
                "Gestión de recursos humanos, gestión de riesgos, gestión de tiempo, gestión del producto.",
                "Gestión de comunicación, gestión de bienes, gestión de alcance, gestión del tiempo",
                "Gestión de Integración, Gestión del alcance, Gestión de tiempo y Gestión de adquisición."
              ],
              "respuestaCorrecta": 3
            },
            {
              "pregunta": "En el esquema de un proceso de iniciación, el patrocinador se encuentra en:",
              "opciones": [
                "Límites internos del proyecto",
                "Límites externos del proyecto",
                "En el ciclo de vida del grupo de procesos",
                "En las áreas que corresponden al control del proyecto"
              ],
              "respuestaCorrecta": 1
            },
            {
              "pregunta": "En el esquema de grupo de procesos de iniciación, el patrocinador se encuentra en:",
              "opciones": [
                "Límites externos del proyecto",
                "En el ciclo de vida de los grupos de procesos",
                "Límites internos del proyecto",
                "En las áreas que correspondan al control del puesto"
              ],
              "respuestaCorrecta": 0
            },
            {
              "pregunta": "Un proyecto está plagado de cambios al proyecto de constitución del proyecto. ¿Quién tiene la responsabilidad principal de decidir si estos cambios son necesarios?",
              "opciones": [
                "El director del proyecto",
                "El equipo del proyecto",
                "El patrocinador",
                "Los interesados"
              ],
              "respuestaCorrecta": 2
            },
            {
              "pregunta": "¿Cuál de los siguientes tipos de dependencia lógica es el más común?",
              "opciones": [
                "Inicio-Inicio",
                "Fin-Inicio",
                "Fin-Fin",
                "Inicio-Fin"
              ],
              "respuestaCorrecta": 1
            },
            {
              "pregunta": "La mecánica de gestión ágil de proyectos está fundamentada en:",
              "opciones": [
                "Pequeños segmentos, ya utilizables, del producto del software desarrollado, con sus especificaciones y superadas las pruebas.",
                "Liberación de responsabilidades, cuya carga se distribuyen de forma coherente, en vez de recaer sobre una sola persona.",
                "Se focaliza en el scrum master, el propietario del producto, miembros del equipo.",
                "La agilidad está dada en la experiencia y experticia de los héroes anónimos del proyecto."
              ],
              "respuestaCorrecta": 3
            },
            {
              "pregunta": "Si nota que en cada proyecto que va a emprender hay ausencia de flexibilidad a cambios, nula capacidad a cambios, deficiente adaptación, pronunciada falta de agilidad; ¿qué debería proponer?",
              "opciones": [
                "Evitar pérdidas de calidad en los entregables",
                "Garantizar la satisfacción del cliente que reciba el producto que tenía en mente.",
                "Gestión de cambios de forma eficiente y efectiva",
                "Utilizar un cóctel de metodologías que cubran todos los flancos de riesgo."
              ],
              "respuestaCorrecta": 3
            },
            {
              "pregunta": "Al estar estructurado en torno a un enfoque flexible, esta forma de gestionar implica que:",
              "opciones": [
                "El producto final puede ser diferente del que se había previsto desde el principio.",
                "El trabajo se aborda en ciclos cortos en pequeña escala, pero consiguen entregar versiones funcionales del producto.",
                "Completar todas las fases para documentar, probar y entregar.",
                "Revisar cada vez que se terminen los entregables y explicar que ya no hay tiempo para recibir cambios",
                "Hacerlo de forma tradicional."
              ],
              "respuestaCorrecta": 0
            },
            {
              "pregunta": "El conjunto de actividades coordinadas que se integran para cumplir un fin específico. Cuenta con: Tiempo, presupuesto y un capital para obtener una ganancia futura; se dice de:",
              "opciones": [
                "Formulación de Proyecto",
                "Análisis económico de Proyecto de inversión.",
                "Estructura del proyecto",
                "Ninguna"
              ],
              "respuestaCorrecta": 1
            },
            {
              "pregunta": "MLTIPLE TDC: A su juicio, escoja algunas de las opciones que ayudarían al éxito o fracaso de su proyecto:",
              "opciones": [
                "Trabajo en equipo.",
                "Decisiones oportunas.",
                "Gestión efectiva con metodologías incorporadas.",
                "Apoyo de gobernabilidad alta empresarial.",
                "Agrupar a los amigos que ya tuvieron éxito en otros proyectos"
              ],
              "respuestaCorrecta": 0
            },
            {
              "pregunta": "¿Cómo menguaría el riesgo en un equipo conflictivo que a su favor tenga un altísimo desenvolvimiento técnico?",
              "opciones": [
                "Reuniones de diálogo en mesa redonda",
                "Revisión del core competence de cada uno y reunificación del equipo",
                "Reuniones de tipo Daily Scrum meeting",
                "Asignar un líder aceptado por todos y mediador-coordinador que garantice atención recíproca",
                "Uso del estilo patriarcal y carácter fustigante sobre los conflictos, despidos a tiempo."
              ],
              "respuestaCorrecta": 3
            },
              {
                "pregunta": "En el levantamiento de requerimiento de técnicas usaría.",
                "opciones": [
                  "Documentación formal de bases documentales: oficios, reglamentos, procesos, base de conocimiento, encuestas, etc.",
                  "Documentación no formal: conversaciones sobre experiencias de usuario.",
                  "Documentación técnica: Gráficos, esquemas, modelos, ejemplos, simuladores, etc.",
                  "Documentación multimedia producida por expertos, explicaciones racionales, prototipos y aplicaciones similares en funcionalidad.",
                  "Todas las anteriores."
                ],
                "respuestaCorrecta": 4
              },
                {
                  "pregunta": "La gestión de un proyecto ágil se basa en:",
                  "opciones": [
                    "Un enfoque impulsado por el valor que permite a los directores del proyecto entregar resultados en condiciones de alta prioridad.",
                    "Un enfoque de no perder dinero, tiempo ni imagen gerencial.",
                    "Un enfoque de trabajo sin distracciones y dentro de los planes, aunque estos no estén tan afinados.",
                    "Presionar a las partes interesadas para que se pongan de acuerdo con los resultados que deberíamos obtener."
                  ],
                  "respuestaCorrecta": 1
                },
                {
                  "pregunta": "En proyectos de tecnología informática, los cambios son constantes, el enfoque ágil acepta estos en cualquier etapa.",
                  "opciones": [
                    "Proponer la entrega en condiciones de aportar el mayor valor de negocio posible.",
                    "Se construirá en base a la obtención de la información en tiempo real.",
                    "Se sirve de una pulida de gestión de materia de costes, tiempo y alcance de proyecto.",
                    "No se aceptará pérdidas de ninguna clase."
                  ],
                  "respuestaCorrecta": 2
                },
                {
                  "pregunta": "Al conjunto de actividades orientadas a levantar y procesar información sobre los diferentes aspectos que tengan relación con un proyecto de inversión.",
                  "opciones": [
                    "Formulación de Proyecto",
                    "Análisis económico del proyecto de inversión",
                    "Estructuración del proyecto",
                    "Ninguna"
                  ],
                  "respuestaCorrecta": 0
                },
                {
                  "pregunta": "Los criterios para diseñar los procesos de la selección de alternativas financieras que permitirán la toma de decisiones para la asignación de los recursos; definen:",
                  "opciones": [
                    "La estructura y arquitectura del proyecto.",
                    "La evaluación del proyecto",
                    "La estructuración del proyecto",
                    "Ninguno"
                  ],
                  "respuestaCorrecta": 1
                },
                {
                  "pregunta": "Cual de las siguientes opciones es correcta en un proyecto de ejecución.",
                  "opciones": [
                    "La ruta crítica ayuda a comprobar cuanto tiempo llevara el proyecto.",
                    "Solo puede haber una ruta crítica",
                    "El diagrama de red cambiara cada vez que cambien la fecha de finalización.",
                    "Un proyecto nunca puede tener una holgura negativa."
                  ],
                  "respuestaCorrecta": 0
                },
                {
                  "pregunta": "Los procesos orientados del producto tienen las siguientes características:",
                  "opciones": [
                    "Son comunes a la mayoría de proyectos",
                    "Su propósito es iniciar, planificar, ejecutar, supervisar y controlar y cerrar un proyecto.",
                    "Son definidos por el ciclo de vida y varían por cada dominio de la aplicación",
                    "Se puede agrupar áreas de conocimientos"
                  ],
                  "respuestaCorrecta": 2
                },
                {
                  "pregunta": "Un ciclo de vida adaptivo procura:",
                  "opciones": [
                    "Generar planes consolidados para mejorar la gestión del riesgo.",
                    "Generar planes detallado en todas las fases para adaptarse a los requisitos.",
                    "Desarrollar planes evolutivos y graduales para adaptación ágil.",
                    "Generar Ciclos iterativos de planificación bajo elaboración progresiva de requisitos."
                  ],
                  "respuestaCorrecta": 3
                },
                {
                  "pregunta": "Las actividades de integración en la gestión del proyecto son realizadas por:",
                  "opciones": [
                    "Los interesados",
                    "El patrocinador",
                    "El director del proyecto",
                    "El equipo."
                  ],
                  "respuestaCorrecta": 1
                },
                {
                  "pregunta": "Durante cual parte del proceso de dirección de proyectos se crea el enunciado del alcance del proyecto:",
                  "opciones": [
                    "Seguimiento y control",
                    "Iniciación",
                    "Ejecución",
                    "Planificación"
                  ],
                  "respuestaCorrecta": 3
                },
                {
                  //  MULTIPLE
                  "pregunta": "MULTIPLE ACT: El ámbito de un proyecto define",
                  "opciones": [
                    "Alcance desde los requisitos",
                    "Costos contratados",
                    "Tiempo determinados en cronogramas",
                    "Objetivo basados en expectativas contra requisitos",
                    "Personas capacitadas para incluirlas en él equipo de proyecto"
                  ],
                  "respuestaCorrecta": 0
                },
                {
                  "pregunta": "Cuál es el principal objetivo de un proyecto de ti",
                  "opciones": [
                    "Entregar un producto con los costos tiempo y alcance pactado",
                    "Entregar el producto o servicio a tiempo",
                    "Entregar el producto que cumpla las expectativas pactadas contractualmente"
                  ],
                  "respuestaCorrecta": 2
                },
                {
                  "pregunta": "¿Cómo menguaría el riesgo en un equipo conflictivo que a su favor tenga un altísimo desenvolvimiento técnico?",
                  "opciones": [
                    "Reuniones de diálogo en mesa redonda",
                    "Revisión del core competencia de cada 1 y reunificación del equipo",
                    "Asignar un líder aceptado por todos y mediador coordinador que garantice atención recíproca",
                    "Uso del estilo patriarcal y carácter fustigante sobre los conflictos",
                    "Ningún"
                  ],
                  "respuestaCorrecta": 2
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

