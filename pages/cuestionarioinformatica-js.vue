<template>
  <div style="display: flex; justify-content: center;">
    <div style="width: 900px; margin-top: 30px;  margin-bottom: 20px">
      <h1>CUESTIONARIO GESTION PROYECTOS</h1>

      <div v-for="(pregunta, index) in preguntas" :key="index" v-if="!calificado">
        <h3>{{ pregunta.pregunta }}</h3>
        <ul>
          <li v-for="(opcion, i) in pregunta.opciones" :key="i">
            <input type="radio" :id="`pregunta-${index}-opcion-${i}`" :name="`pregunta-${index}`" :value="i" v-model="respuestas[index]">
            <label :for="`pregunta-${index}-opcion-${i}`">{{ opcion }}</label>
          </li>
        </ul>
      </div>
      <div>
        <button @click="calificar">Enviar respuestas</button>
        <button @click="reiniciar">Reiniciar cuestionario</button>
      </div>
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
      lucho: [
          {
            "pregunta": "Entre los principios básicos de la gestión de proyectos está el que se denomina “triple restricción” ¿qué implica?",
            "opciones": [
              "La gestión de cronograma y cuadros de Gantt",
              "La gestión de interesado y stakeholders",
              "La gestión de cronograma, alcance y tiempo",
              "La gestión de dirección del PMBOOK"
            ],
            "respuestaCorrecta": 2
          },
          {
            "pregunta": "Un principio de cualquier proyecto está dado por sus objetivos. ¿Cuál es el correcto?",
            "opciones": [
              "Es fundamental alcanzar la situación deseada propuesta por el proyecto",
              "Es necesario alcanzar los objetivos de alcance, costo y tiempo",
              "El proyecto puede ir más allá de la triple restricción hacia la triple restricción ampliada",
              "El proyecto puede evolucionar gradualmente sobre la operación de la empresa"
            ],
            "respuestaCorrecta": 0
          },
          {
            "pregunta": "¿Cuándo es adecuado gestionar un portafolio de proyectos?",
            "opciones": [
              "Hay una diversidad de proyectos estratégicos que requieren ser alineados",
              "Es necesario establecer un balance entre diferentes proyectos de una organización",
              "Se requiere optimizarlos y lograr beneficios conjuntos",
              "Los proyectos tienen temporalidad superpuesta"
            ],
            "respuestaCorrecta": 0
          },
          {
            "pregunta": "¿Cuál es una característica de los proyectos?",
            "opciones": [
              "Por lo general, crean un resultado que tiene temporalidad",
              "Crean entregables que se repiten y se miden en cada fase del proyecto",
              "Son respuestas a las necesidades de los stakeholders",
              "Tienen resultados que se van elaborando progresivamente"
            ],
            "respuestaCorrecta": 3
          },
          {
            "pregunta": "Existen diferentes formas de poder a disposición de los directores de proyecto. Una característica de autoridad es el “experto”. ¿Con qué tiene que ver?",
            "opciones": [
              "Aquel con control de la distribución de información",
              "Aquel orientado a recompensa o reconocimiento",
              "Aquel con respecto ganado con una situación excepcional",
              "Aquel con información adquirida, experiencia o certificación"
            ],
            "respuestaCorrecta": 3
          },
          {
            "pregunta": "¿Cuáles son algunos factores que influyen en la elección de estilo de liderazgo?",
            "opciones": [
              "La dirección mediante el poder de la posición",
              "Personalidad creativa, orientada al servicio y de pensamiento sistémico",
              "Orientación centrada en la metas y logros para determinar recompensas",
              "La concentración en el resultado final"
            ],
            "respuestaCorrecta": 1
          },
          {
            "pregunta": "Existen algunos factores que contribuyen al éxito de una negociación, ¿cuál de los siguientes NO es uno de ellos?",
            "opciones": [
              "La contraparte debe percibir que las concesiones son importantes",
              "Debe existir continuamente una comunicación eficiente",
              "Es mejor dejar de lado rápidamente las discusiones que no aportan valor",
              "Enfocarse en las restricciones conocidas del proyecto"
            ],
            "respuestaCorrecta": 3
          }

      ],
      nuevasPreguntas: [

        {
          "pregunta": "Los pasos para definir el cronograma del proyecto son los siguientes:",
          "opciones": [
            "Definir listado de entregables, secuenciar actividades, definir duración de actividades, elaborar cronograma.",
            "Estimar recursos, definir listado de actividades, definir duración de actividades, secuenciar actividades.",
            "Definir listado de actividades, secuenciar actividades, estimar recursos, definir duración de actividades, elaborar cronograma.",
            "Elaborar cronograma, definir listado de actividades, estimar recursos, secuenciar actividades."
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Un índice de desempeño del costo CPI de 0.89 significa:",
          "opciones": [
            "El proyecto está progresando al 89% del ritmo previsto.",
            "El proyecto está obteniendo 0.89 ctvs de valor por cada dólar gastado.",
            "Una vez completado el proyecto habremos gastado el 8% más de los planificado",
            "El proyecto está bajo presupuesto por un 11%."
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "¿Cuál de las siguientes opciones es VERDADERA acerca del desarrollo del acta de constitución del proyecto?",
          "opciones": [
            "El acta de constitución del proyecto es aprobada por el equipo del proyecto.",
            "El director del proyecto aprueba el acta de constitución del proyecto.",
            "El acta de constitución del proyecto es una entrada para el proceso de planificación.",
            "El director del proyecto crea el acta de constitución del proyecto y el patrocinador la aprueba."
          ],
          "respuestaCorrecta": 3
        },


        {
          "pregunta": "El enunciado del alcance del proyecto es una de las salidas del proceso de “Definicion del Alcance”. Entre otras consideraciones sugiere:",
          "opciones": [
            "Dividir el proyecto o entregable principal en fases mas pequeñas para facilitar la administración.",
            "Establecer los recursos necesarios para cumplir con el alcance.",
            "Definir el presupuesto necesario para el alcance definido.",
            "Establecer las restricciones y supuestos del alcance del proyecto."
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Una de las herramientas mas importantes en la creación del EDT es la descomposición en paquetes de trabajo, lo que implica:",
          "opciones": [
            "Dividir el proyecto en diferentes fases para su administración.",
            "Asignar recursos a cada paquete de trabajo definido.",
            "Estimar el esfuerzo en un determinado nivel.",
            "Definir los entregables principales del proyecto."
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Cual de las siguientes es la MEJOR herramienta de dirección de proyectos para usar con el fin de determinar el mayor periodo de tiempo o duración que llevara el proyecto?",
          "opciones": [
            "Gráfico de Gantt",
            "Histograma de recursos",
            "Diagrama de Red",
            "Análisis PERT"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "¿Cuánto dura un hito?",
          "opciones": [
            "Depende del tamaño del proyecto.",
            "No tiene duración",
            "Varía dependiendo de la fase del proyecto.",
            "Depende de los recursos asignados."
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "Suponga que esta iniciando la planificación de un proyecto en el que se le nombra a usted como Director dada su experiencia anterior. Le han indicado solo los requisitos a alto nivel y al momento dispone de recursos limitados. En este momento, cual tipo de estimación seria la mas indicada.",
          "opciones": [
            "Estimación paramétrica",
            "Estimación análoga",
            "Estimación ascendente",
            "Estimación por expertos"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "Cual de las siguientes opciones es CORRECTA en un proyecto en ejecución:",
          "opciones": [
            "La ruta crítica ayuda a comprobar cuanto tiempo llevara el proyecto",
            "La ruta crítica define las dependencias entre las tareas",
            "Solo puede haber una ruta crítica en un proyecto",
            "La ruta crítica siempre es la más corta en términos de duración"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "El acta de constitución es un documento formal que reconoce la existencia del proyecto. Este documento confiere las siguientes atribuciones.",
          "opciones": [
            "Define los objetivos y entregables del proyecto",
            "Confiere al director del proyecto la autoridad para asignar recursos de la organización al proyecto",
            "Establece las restricciones de tiempo, costo y alcance del proyecto",
            "Define las partes interesadas y sus roles y responsabilidades en el proyecto"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "El juicio de expertos es un_____del proceso de definición del alcance",
          "opciones": [
            "Resultado",
            "Entrada",
            "Herramienta/técnica",
            "Criterio"
          ],
          "respuestaCorrecta": 2
        },


        {
          "pregunta": "Durante una reunión del equipo de proyecto, un miembro del equipo sugiere una mejora para el alcance que va más allá del alcance del acta de constitución del proyecto. El director del proyecto señala que el equipo necesita concentrarse solo en el trabajo solicitado, esto es ejemplo de:",
          "opciones": [
            "Gestión de alcance",
            "Gestión de calidad",
            "Gestión de riesgos",
            "Gestión de comunicaciones"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "La evaluación, estructuración y formulación de un proyecto es desde todo punto de vista:",
          "opciones": [
            "Una metodología",
            "Una técnica",
            "Un proceso",
            "Una herramienta"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Cuáles son las disciplinas o áreas de conocimiento fundamentales que debe enfrentar ante la estructuración de un proyecto en su concepción:",
          "opciones": [
            "Costos, tiempo, alcance",
            "Calidad, recursos humanos, comunicaciones",
            "Riesgos, adquisiciones, integración",
            "Interesados, ciclo de vida, adaptabilidad"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Realizar un análisis amplio de los resultados financieros, económicos y sociales de inversión en un proyecto se dice de:",
          "opciones": [
            "Estudio de factibilidad",
            "Análisis SWOT",
            "Estudio de mercado",
            "Análisis de riesgo"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "En el esquema de un proceso de iniciación, el patrocinador se encuentra en:",
          "opciones": [
            "Los límites internos del proyecto",
            "Los límites externos del proyecto",
            "En el ciclo de vida del grupo de procesos",
            "En las áreas que corresponden al control del proyecto"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "Un proyecto está plagado de cambios al proyecto de constitución del proyecto. ¿Quién tiene la responsabilidad de decidir si estos cambios son necesarios?",
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
            "INICIO-INICIO",
            "FIN-INICIO",
            "FIN-FIN",
            "INICIO-FIN"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "La mecánica de la gestión ágil de proyectos está fundamentada en:",
          "opciones": [
            "La agilidad está dada en la experiencia y experticia de los héroes anónimos del proyecto.",
            "La implementación de técnicas tradicionales de gestión de proyectos.",
            "La priorización de la documentación sobre la comunicación directa.",
            "El uso extensivo de software y herramientas de seguimiento de proyectos."
          ],
          "respuestaCorrecta": 0
        },

        {
          "pregunta": "Si nota que en cada proyecto que usted va a emprender hay ausencia de flexibilidad a cambios, nula capacidad de cambios, deficiente adaptación, pronunciada falta de agilidad; ¿qué debería proponer?",
          "opciones": [
            "Utilizar un coctel de metodologías que cubran todos los flancos de riesgo.",
            "Ignorar las limitaciones y seguir adelante con el proyecto.",
            "Limitar la interacción con los stakeholders para evitar distracciones.",
            "Concentrarse solo en la gestión del alcance y evitar cambios."
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "A su juicio, escoja algunas de las opciones que ayudarían al éxito o fracaso de su proyecto.",
          "opciones": [
            "Trabajo en equipo, decisiones oportunas, Gestión efectiva con metodologías incorporadas.",
            "Limitar la comunicación con el equipo, evitar reuniones regulares, no establecer un plan claro.",
            "Priorizar la documentación extensiva sobre la entrega efectiva del proyecto.",
            "Evitar la retroalimentación de los stakeholders y seguir adelante sin revisiones."
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Las actividades de integración en la gestión del proyecto son realizadas por:",
          "opciones": [
            "El patrocinador",
            "El director del proyecto",
            "El equipo del proyecto",
            "Los interesados"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Durante ¿cuál parte del proceso de dirección de proyectos se crea el enunciado del alcance del proyecto?",
          "opciones": [
            "Planificación",
            "Iniciación",
            "Ejecución",
            "Monitoreo y Control"
          ],
          "respuestaCorrecta": 0
        },

        {
          "pregunta": "Los proyectos con ciclo de vida predictivo tienen la siguiente característica:",
          "opciones": [
            "Se adaptan constantemente a los cambios.",
            "Están orientados a un plan definido.",
            "No requieren una planificación detallada.",
            "Se basan en un enfoque ágil."
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "La matriz de procesos para la dirección de proyectos del PMBok se estructura a partir",
          "opciones": [
            "La relación entre las fases del proyecto y las áreas de conocimiento.",
            "La relación entre el ciclo de vida del proyecto y los grupos de procesos.",
            "La relación entre grupos de procesos y áreas de conocimiento.",
            "La relación entre los stakeholders y las áreas de conocimiento."
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Las áreas de gestión de conocimiento del PMBoK está constituido por:",
          "opciones": [
            "Un total de 9 áreas",
            "Un total de 12 áreas",
            "Un total de 10 áreas",
            "Un total de 11 áreas"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "El PMBoK Guide es un estándar para la gerencia de proyectos cuya misión es lograr la excelencia mundial en la gerencia de proyectos. Este cuerpo de conocimiento está patrocinado por:",
          "opciones": [
            "El Project Management Association",
            "El Project Management Council",
            "El Project Management Institute",
            "El Project Management Consortium"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "Cuál de los siguientes pilares del manifiesto ágil es más valorado en esta guía.",
          "opciones": [
            "Individuos e iteraciones.",
            "Procesos y herramientas.",
            "Documentación exhaustiva.",
            "Colaboración con el cliente."
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Una de las principales ventajas de la organización matricial es:",
          "opciones": [
            "Mayor flexibilidad en la asignación de recursos.",
            "Mejorar el control del Project manager sobre los recursos.",
            "Aumento de la comunicación entre departamentos.",
            "Mayor autonomía de los equipos de proyecto."
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "En una organización proyectizada el equipo de proyecto:",
          "opciones": [
            "Siempre tendrá una posición fija.",
            "Tendrá una posición rotativa.",
            "Dependerá directamente del director del proyecto.",
            "No siempre tendrá una posición fija."
          ],
          "respuestaCorrecta": 3
        },
        {
          "pregunta": "Durante que fase del ciclo de vida se crea el presupuesto detallado del proyecto:",
          "opciones": [
            "Ejecución",
            "Iniciación",
            "Cierre",
            "Planeamiento"
          ],
          "respuestaCorrecta": 3
        },
        {
          "pregunta": "El Acta de constitución se crea durante que fase del ciclo de vida:",
          "opciones": [
            "Planeamiento",
            "Iniciación",
            "Ejecución",
            "Cierre"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "El calendario detallado del proyecto solo se puede crear después de haber elaborado:",
          "opciones": [
            "El presupuesto del proyecto.",
            "El análisis de riesgos.",
            "EDT",
            "El plan de recursos humanos."
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "La agilidad implica entre otras cosas:",
          "opciones": [
            "Un enfoque estricto y poco flexible en la ejecución",
            "Evitar la interacción y feedback con el cliente",
            "La adaptabilidad para crear un resultado",
            "La priorización de documentación extensa en el proyecto"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "El control de procesos que gestiona SCRUM se basa en ciertas teorías reconocidas:",
          "opciones": [
            "El conocimiento basado en la experiencia que proporciona la experimentación del proceso",
            "La gestión basada en jerarquías estrictas y roles rígidos",
            "El enfoque en la documentación detallada y menos en la colaboración",
            "La teoría de evitar la adaptabilidad y seguir un proceso estricto"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "El dueño del proceso es un rol de importancia en el esquema SCRUM, bajo su responsabilidad se tiene:",
          "opciones": [
            "La organización y facilitación de todas las reuniones SCRUM",
            "La gestión y seguimiento de producto backlog.",
            "La resolución de conflictos internos y negociaciones con el cliente",
            "La codificación y prueba de todas las características del producto"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "Uno de los pilares de SCRUM es la inspección, esta está orientada a lo siguiente en un proyecto:",
          "opciones": [
            "Evitar cualquier cambio y seguir el plan inicial",
            "Evaluar el progreso del trabajo y detectar variaciones",
            "Evitar la retroalimentación y seguir adelante con el proyecto",
            "Inspeccionar y criticar el trabajo de cada miembro del equipo"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "Un bloque de tiempo es un evento que tiene algunas características tales como:",
          "opciones": [
            "Se pueden extender según las necesidades del equipo",
            "Tienen una duración fija y no pueden acortarse ni alargarse",
            "Son flexibles y pueden variar según las necesidades del cliente",
            "Se utilizan para planificar el tiempo de descanso del equipo"
          ],
          "respuestaCorrecta": 1
        }
      ],
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
        },
        {
          "pregunta": "Existen algunas características propias de un proyecto, tales como:",
          "opciones": [
            "Un producto es único e irrepetible, se lo produce progresivamente y requiere participación multidisciplinaria",
            "Es temporal y finito, requiere una plataforma de software definida, su elaboración es progresiva",
            "Necesariamente tiene incertidumbre, requiere operaciones rutinarias definidas, tiene inicio y fin definido",
            "Su producto es único e irrepetible, requiere una plataforma de software definida, tiene inicio y fin definido"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "La gestión de portafolios da soporte a la dirección de la empresa para:",
          "opciones": [
            "Gestionar el alcance a los proyectos integrantes",
            "Obtener beneficios y eficiencia que no se lograrían cuando los proyectos se gestionan de manera individual",
            "Centralizar la gestión del riesgo agregado de todos los componentes",
            "Planificar y elaborar información a lo largo del ciclo de vida del proyecto"
          ],
          "respuestaCorrecta": 2
        },
        {
          "pregunta": "En las organizaciones con estructura de matriz-fuerte es común lo siguiente:",
          "opciones": [
            "La gestión del presupuesto es una responsabilidad del sponsor",
            "La gestión del presupuesto es una responsabilidad del director de proyecto",
            "La gestión del presupuesto es una responsabilidad del gerente financiero",
            "La gestión del presupuesto es una responsabilidad del comité de proyecto"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "Entre las características más destacadas de las PMOs podemos distinguir:",
          "opciones": [
            "Integra las políticas organizacionales para cumplir objetivos estratégicos",
            "Es parte de la estructura matricial de la organización",
            "Está creada fundamentalmente para la gestión de portafolios",
            "Juega un papel preponderante en la alineación estratégica de los proyectos"
          ],
          "respuestaCorrecta": 3
        },
        {
          "pregunta": "Las aristas principales relacionadas con las competencias del Director de Proyectos se relacionan con:",
          "opciones": [
            "Los conocimientos, habilidades y comportamiento en el campo específico de la dirección de proyectos",
            "La gestión de medición y control sobre los elementos de la triple restricción",
            "El control y medición del proyecto en periodos determinados por la Dirección",
            "La gestión de negociación y capacidad de administración de recursos que debe tener el director"
          ],
          "respuestaCorrecta": 0
        },
        {
          "pregunta": "Dentro del formulario de negociación se sugieren algunos elementos de apoyo, entre ellos:",
          "opciones": [
            "Presupuesto definido del proyecto",
            "Conocer o inferir objetivos de la contraparte",
            "Establecer claramente los límites de la negociación",
            "Asignar un equipo técnico experimentado"
          ],
          "respuestaCorrecta": 1
        },
        {
          "pregunta": "La organización de consultoría europea (Standish Group) define que para que un proyecto sea exitoso debe contener elementos, tales como:",
          "opciones": [
            "Una clara definición de requerimientos y una planeación adecuada",
            "Estimular las concesiones de cada parte para llegar a un punto de equilibrio",
            "Establecer un equipo auto-organizado con suficiente experiencia",
            "Priorizar la interacción con el cliente antes que cualquier documentación"
          ],
          "respuestaCorrecta": 0
        }

      ],
      respuestas: [],
      calificado: false
    }
  },
  methods: {
    reiniciar () {
      this.respuestas = []
      this.calificado = false
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
  },
  mounted() {
    // ordenar aleatoreamente las preguntas
    if ( this.$route.query.type === 'nuevas' ) {
      this.preguntas = this.nuevasPreguntas
    }
    if ( this.$route.query.type === 'lucho' ) {
      this.preguntas = this.lucho
    }

    this.preguntas = this.preguntas.sort(() => Math.random() - 0.5)
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

