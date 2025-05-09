<template>
  <div class="jumbotron">
    <div class="container-fluid h-100">
      <div class="row h-100 align-items-center justify-content-center">
        <div class="col-12 col-xl-10">
          <div class="text-center mb-4">
            <img src="/ICONO-AIDIN-512.png" alt="Logo" class="img-fluid mb-3" style="max-width: 75px;">
            <h1 style="font-family: 'Amaranth', sans-serif; font-weight: bold; color: #3b56a1;">Evaluaciones</h1>
            <div class="input-group mb-3" style="max-width: 300px; margin: 0 auto;">
              <input 
                type="text" 
                class="form-control" 
                placeholder="Buscar alumno..." 
                v-model="searchQuery"
                @input="handleSearch"
              >
            </div>
          </div>
          <div class="d-flex align-items-start flex-column flex-lg-row">
            <div class="table-responsive mb-3 mb-lg-0">
              <table class="table table-bordered">
              <thead>
                <tr>
                  <th class="fixed-column" rowspan="2">ALUMNOS</th>
                  <th data-column-type="tema">
                    TEMA
                  </th>
                  <th colspan="2" data-column-type="enigma" :class="{ 'collapsed': !isExpanded1 }">ENIGMA</th>
                  <th data-column-type="esquema" :class="{ 'collapsed': !isExpanded1 }">ESQUEMA</th>
                  <th colspan="2" data-column-type="explica" :class="{ 'collapsed': !isExpanded1 }">EXPLICA EL ALUMNO</th>
                  <th colspan="5" data-column-type="coding" :class="{ 'collapsed': !isExpanded1 }">CODING</th>
                  <th data-column-type="tema">
                    TEMA
                  </th>
                  <th colspan="2" data-column-type="enigma" :class="{ 'collapsed': !isExpanded2 }">ENIGMA</th>
                  <th data-column-type="esquema" :class="{ 'collapsed': !isExpanded2 }">ESQUEMA</th>
                  <th colspan="2" data-column-type="explica" :class="{ 'collapsed': !isExpanded2 }">EXPLICA EL ALUMNO</th>
                  <th colspan="5" data-column-type="coding" :class="{ 'collapsed': !isExpanded2 }">CODING</th>

                </tr>
                <tr>
                  <th data-column-type="tema" @click="isExpanded1 = !isExpanded1" style="cursor: pointer;">
                    EL CICLO DEL AGUA
                    <span class="toggle-icon">{{ isExpanded1 ? '▼' : '▶' }}</span>
                  </th>
                  <th data-column-type="enigma" :class="{ 'collapsed': !isExpanded1 }" 
                      data-bs-toggle="tooltip" 
                      data-bs-placement="top" 
                      title="¿Por qué los mares no crecen sin parar? ¿Por qué los ríos no se vacían?">
                      Enigma 1
                  </th>
                  <th data-column-type="enigma" :class="{ 'collapsed': !isExpanded1 }"
                      data-bs-toggle="tooltip" 
                      data-bs-placement="top" 
                      title="Si el agua de los ríos, la nieve y la lluvia es dulce, ¿cómo es posible que el agua del mar sea salada?">
                      Enigma 2
                  </th>
                  <th data-column-type="esquema" :class="{ 'collapsed': !isExpanded1 }"
                      data-bs-toggle="tooltip" 
                      data-bs-placement="top" 
                      title="El viaje de una gota de agua">
                      Esquema 1
                  </th>
                  <th data-column-type="explica" :class="{ 'collapsed': !isExpanded1 }" data-bs-toggle="tooltip" title="¿Por qué los mares no se desbordan?">Explica 1</th>
                  <th data-column-type="explica" :class="{ 'collapsed': !isExpanded1 }" data-bs-toggle="tooltip" data-bs-placement="top" title="¿Por qué el mar es salado?">Explica 2</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded1 }" data-bs-toggle="tooltip" data-bs-placement="top" title="CONDENSACIÓN">Coding 1</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded1 }" data-bs-toggle="tooltip" data-bs-placement="top" title="NUBES">Coding 2</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded1 }" data-bs-toggle="tooltip" data-bs-placement="top" title="PRECIPITACIÓN">Coding 3</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded1 }" data-bs-toggle="tooltip" data-bs-placement="top" title="ESCORRENTÍA">Coding 4</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded1 }" data-bs-toggle="tooltip" data-bs-placement="top" title="EVAPORACIÓN">Coding 5</th>
                  <th data-column-type="tema" @click="isExpanded2 = !isExpanded2" style="cursor: pointer;">
                    EL CICLO DEL AGUA 2
                    <span class="toggle-icon">{{ isExpanded2 ? '▼' : '▶' }}</span>
                  </th>
                  <th data-column-type="enigma" :class="{ 'collapsed': !isExpanded2 }"
                      data-bs-toggle="tooltip" 
                      data-bs-placement="top" 
                      title="¿Por qué los mares no crecen sin parar? ¿Por qué los ríos no se vacían?">
                      Enigma 1
                  </th>
                  <th data-column-type="enigma" :class="{ 'collapsed': !isExpanded2 }"
                      data-bs-toggle="tooltip" 
                      data-bs-placement="top" 
                      title="Si el agua de los ríos, la nieve y la lluvia es dulce, ¿cómo es posible que el agua del mar sea salada?">
                      Enigma 2
                  </th>
                  <th data-column-type="esquema" :class="{ 'collapsed': !isExpanded2 }"
                      data-bs-toggle="tooltip" 
                      data-bs-placement="top" 
                      title="El viaje de una gota de agua">
                      Esquema 1
                  </th>
                  <th data-column-type="explica" :class="{ 'collapsed': !isExpanded2 }" data-bs-toggle="tooltip" data-bs-placement="top" title="¿Por qué los mares no se desbordan?">Explica 1</th>
                  <th data-column-type="explica" :class="{ 'collapsed': !isExpanded2 }" data-bs-toggle="tooltip" data-bs-placement="top" title="¿Por qué el mar es salado?">Explica 2</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded2 }" data-bs-toggle="tooltip" data-bs-placement="top" title="CONDENSACIÓN">Coding 1</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded2 }" data-bs-toggle="tooltip" data-bs-placement="top" title="NUBES">Coding 2</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded2 }" data-bs-toggle="tooltip" data-bs-placement="top" title="PRECIPITACIÓN">Coding 3</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded2 }" data-bs-toggle="tooltip" data-bs-placement="top" title="ESCORRENTÍA">Coding 4</th>
                  <th data-column-type="coding" :class="{ 'collapsed': !isExpanded2 }" data-bs-toggle="tooltip" data-bs-placement="top" title="EVAPORACIÓN">Coding 5</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="student in filteredStudents" :key="student.id">
                  <td class="fixed-column" 
                      @click="toggleStudentFilter(student)" 
                      :class="{ 'selected-student': selectedStudent === student.id }"
                      style="cursor: pointer;">
                    {{ student.name }}
                  </td>
                  <td data-cell-type="tema"></td>
                  <td v-for="(activity, index) in student.activities" :key="index"
                      @click="openModal(student, activity, index + 1)"
                      style="cursor: pointer;"
                      class="activity-cell"
                      :data-cell-type="getCellType(index)">
                    {{ activity.grade || '-' }}
                    <span :class="['status-circle', getStatusClass(activity.status)]"></span>
                  </td>
                  <td data-cell-type="tema"></td>
                  <td v-for="(activity, index) in student.activities2" :key="index"
                      @click="openModal(student, activity, index + 1)"
                      style="cursor: pointer;"
                      class="activity-cell"
                      :data-cell-type="getCellType(index)">
                    {{ activity.grade || '-' }}
                    <span :class="['status-circle', getStatusClass(activity.status)]"></span>
                  </td>
                </tr>
              </tbody>
            </table>
            </div>
            <div class="legend-container ms-4">
              <h4 class="mb-3 text-center" style="font-family: 'Amaranth', sans-serif; font-weight: bold; color: #3b56a1;">ACTIVIDADES</h4>
              <div class="legend-item">
                <span class="status-circle bg-secondary"></span>
                <span class="ms-2">No activada</span>
              </div>
              <div class="legend-item">
                <span class="status-circle bg-danger"></span>
                <span class="ms-2">No entregada por el alumno</span>
              </div>
              <div class="legend-item">
                <span class="status-circle bg-info"></span>
                <span class="ms-2">Entregada pero no evaluada por AIDIN</span>
              </div>
              <div class="legend-item">
                <span class="status-circle bg-primary"></span>
                <span class="ms-2">Evaluada por AIDIN</span>
              </div>
              <div class="legend-item">
                <span class="status-circle bg-success"></span>
                <span class="ms-2">Evaluada por el profesor</span>
              </div>
            </div>
          </div>

          <!-- Modal -->
          <div class="modal fade" id="evaluationModal" tabindex="-1">
            <div class="modal-dialog modal-lg">
              <div class="modal-content">
                <div class="modal-header">
                  <h5 class="modal-title">
                    {{ 
                      selectedActivity && (
                        selectedActivity.enigmaNumber === 1 ? 'ENIGMA 1: ¿Por qué los mares no crecen sin parar? ¿Por qué los ríos no se vacían?' :
                        selectedActivity.enigmaNumber === 2 ? 'ENIGMA 2: Si el agua de los ríos, la nieve y la lluvia es dulce, ¿cómo es posible que el agua del mar sea salada?' :
                        selectedActivity.type === 'esquema' ? 'ESQUEMA 1: El viaje de una gota de agua' :
                        selectedActivity.type === 'explica' && selectedActivity.explicaNumber === 1 ? 'EXPLICA EL ALUMNO 1: ¿Por qué los mares no se desbordan?' :
                        selectedActivity.type === 'explica' && selectedActivity.explicaNumber === 2 ? 'EXPLICA EL ALUMNO 2: ¿Por qué el mar es salado?' :
                        selectedActivity.type === 'coding' && (selectedActivity.enigmaNumber === 6 || selectedActivity.enigmaNumber === 18) ? 'CODING 1: CONDENSACIÓN' :
                        selectedActivity.type === 'coding' && (selectedActivity.enigmaNumber === 7 || selectedActivity.enigmaNumber === 19) ? 'CODING 2: NUBES' :
                        selectedActivity.type === 'coding' && (selectedActivity.enigmaNumber === 8 || selectedActivity.enigmaNumber === 20) ? 'CODING 3: PRECIPITACIÓN' :
                        selectedActivity.type === 'coding' && (selectedActivity.enigmaNumber === 9 || selectedActivity.enigmaNumber === 21) ? 'CODING 4: ESCORRENTÍA' :
                        selectedActivity.type === 'coding' && (selectedActivity.enigmaNumber === 10 || selectedActivity.enigmaNumber === 22) ? 'CODING 5: EVAPORACIÓN' :
                        'Evaluación'
                      )
                    }}
                  </h5>
                  <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body" v-if="selectedActivity">
                  <div v-if="selectedActivity.status === 'notStarted'" class="d-flex flex-column align-items-center justify-content-center" style="height: 200px;">
                    <h2 class="text-center mb-3" style="font-family: 'Amaranth', sans-serif; font-weight: bold; color: #dc3545;">ACTIVIDAD NO ACTIVADA</h2>
                    <img src="/actividad-bloqueada.png" alt="Actividad bloqueada" style="width: 100px;">
                  </div>
                  <div v-else-if="selectedActivity.status === 'pending'" class="d-flex flex-column align-items-center justify-content-center" style="height: 200px;">
                    <h2 class="text-center mb-3" style="font-family: 'Amaranth', sans-serif; font-weight: bold; color: #dc3545;">ACTIVIDAD NO ENTREGADA POR EL ALUMNO</h2>
                    <img src="/NO-ENTREGADA.png" alt="Actividad no entregada" style="width: 100px;">
                  </div>
                  <iframe v-else-if="selectedActivity.chatUrl" :src="selectedActivity.chatUrl" class="w-100" style="height: 400px;"></iframe>
                  <div class="mt-3" v-if="selectedActivity.status !== 'notStarted'">
                    <div class="mb-3" v-if="selectedActivity.status === 'aiEvaluated' || selectedActivity.status === 'submitted'">
                      <label class="form-label">Nota AIDIN</label>
                      <div class="input-group">
                        <input type="text" class="form-control" :value="selectedActivity.status === 'submitted' ? '-- (No evaluada por AIDIN)' : selectedActivity.grade" readonly>
                        <div class="input-group-text" v-if="selectedActivity.status === 'aiEvaluated'">
                          <input type="checkbox" v-model="selectedActivity.accepted" @change="handleAcceptedChange">
                        </div>
                      </div>
                    </div>
                    <div class="mb-3">
                      <label class="form-label">Nota del profesor</label>
                      <input type="number" class="form-control" v-model="selectedActivity.teacherGrade" :disabled="selectedActivity.accepted">
                    </div>
                    <div class="mb-3">
                      <label class="form-label">Comentarios</label>
                      <textarea class="form-control" v-model="selectedActivity.comments"></textarea>
                    </div>
                  </div>
                </div>
                <div class="modal-footer">
                  <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">CERRAR</button>
                  <button v-if="selectedActivity && selectedActivity.status !== 'notStarted'" type="button" class="btn btn-primary" @click="saveAndCloseModal">GUARDAR</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted, computed } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import * as bootstrap from 'bootstrap'

export default {
  name: 'EvaluationTable',
  setup() {
    const isExpanded1 = ref(false)
    const isExpanded2 = ref(false)
    const selectedStudent = ref(null)
    const searchQuery = ref('')
    const students = ref([
      { id: 1, name: 'Patricia Álvarez', 
        activities: Array(10).fill().map((_, index) => ({ 
          status: 'pending', 
          chatUrl: index === 1 ? 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=9' :
                  index === 0 ? 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' : 
                  '',
          text: 'Explica el alumno 1' 
        })), 
        activities2: Array(10).fill().map((_, index) => ({ 
          status: (index >= 6 || index === 6) ? 'notStarted' : 'pending', // Coding activities and specifically Coding 1
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        }))
      },
      { id: 2, name: 'Fernando Castro', 
        activities: Array(10).fill().map((_, index) => ({ 
          status: 'submitted', 
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })), 
        activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'submitted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        }))
      },
      { id: 3, name: 'Andrés Delgado', 
        activities: Array(10).fill().map((_, index) => ({ 
          status: 'aiEvaluated', 
          grade: 8, 
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })), 
        activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'aiEvaluated',
          grade: index >= 6 ? undefined : 8,
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        }))
      },
      { id: 4, name: 'Carmen Díaz', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 5, name: 'David Fernández', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 6, name: 'Ana García', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 7, name: 'Pablo Gómez', activities: Array(10).fill({ status: 'submitted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'submitted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 8, name: 'Isabel Jiménez', activities: Array(10).fill({ status: 'submitted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'submitted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 9, name: 'María López', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 10, name: 'Juan Martínez', activities: Array(10).fill({ status: 'submitted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'submitted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 11, name: 'José Moreno', activities: Array(10).fill({ status: 'pending', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'pending',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 12, name: 'Roberto Muñoz', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 13, name: 'Lucía Navarro', activities: Array(10).fill({ status: 'aiEvaluated', grade: 9, chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'aiEvaluated',
          grade: index >= 6 ? undefined : 9,
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 14, name: 'Cristina Ortiz', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 15, name: 'Sofia Pérez', activities: Array(10).fill({ status: 'pending', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'pending',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 16, name: 'Alberto Romero', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 17, name: 'Carlos Rodríguez', activities: Array(10).fill({ status: 'pending', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'pending',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 18, name: 'Miguel Ruiz', activities: Array(10).fill({ status: 'aiEvaluated', grade: 7, chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'aiEvaluated',
          grade: index >= 6 ? undefined : 7,
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 19, name: 'Laura Sánchez', activities: Array(10).fill({ status: 'aiEvaluated', grade: 8, chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: index >= 6 ? 'notStarted' : 'aiEvaluated',
          grade: index >= 6 ? undefined : 8,
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) },
      { id: 20, name: 'Elena Torres', activities: Array(10).fill({ status: 'notStarted', chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8' }), activities2: Array(10).fill().map((_, index) => ({ 
          status: 'notStarted',
          chatUrl: 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8'
        })) }
    ])

    const selectedActivity = ref(null)

    const getStatusClass = (status) => {
      const classes = {
        notStarted: 'bg-secondary',
        pending: 'bg-danger',
        submitted: 'bg-info',
        aiEvaluated: 'bg-primary',
        teacherEvaluated: 'bg-success'
      }
      return classes[status]
    }

    const openModal = (student, activity, index) => {
      const type = getCellType(index - 1);
      const explicaNumber = type === 'explica' ? (index === 4 || index === 16 ? 1 : 2) : null;

      // Asignar la URL correcta según el tipo de actividad
      let chatUrl = activity.chatUrl;
      if (type === 'enigma') {
        if (index === 2 || index === 14) { // Enigma 2
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=9';
        } else if (index === 1 || index === 13) { // Enigma 1
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=8';
        }
      } else if (type === 'esquema') {
        if (index === 3 || index === 15) { // Esquema 1
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=14';
        }
      } else if (type === 'explica') {
        if (index === 4 || index === 16) { // Explica 1
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=11';
        } else if (index === 5 || index === 17) { // Explica 2
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=10';
        }
      } else if (type === 'coding') {
        if (index === 6 || index === 18) { // Coding 1
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=21';
        } else if (index === 7 || index === 19) { // Coding 2
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=22';
        } else if (index === 8 || index === 20) { // Coding 3
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=23';
        } else if (index === 9 || index === 21) { // Coding 4
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=24';
        } else if (index === 10 || index === 22) { // Coding 5
          chatUrl = 'https://courses.steamfuture.academy/tools_steam/aidin-chatbot/gpt/?idchat=25';
        }
      }

      selectedActivity.value = {
        ...activity, 
        studentName: student.name, 
        enigmaNumber: index, 
        type, 
        explicaNumber,
        chatUrl,
        teacherGrade: activity.status === 'aiEvaluated' ? activity.grade : ''
      }
      const modalElement = document.getElementById('evaluationModal')
      if (!modalElement._bsModal) {
        modalElement._bsModal = new bootstrap.Modal(modalElement, {
          backdrop: 'static',
          keyboard: false
        })
      }
      modalElement._bsModal.show()
    }

    const getCellType = (index) => {
      if (index < 2) return 'enigma'
      if (index === 2) return 'esquema'
      if (index === 3 || index === 4) return 'explica'
      return 'coding'
    }

    const isExplicaAlumno1 = (index) => index === 3; 

    onMounted(() => {
      import('bootstrap/dist/js/bootstrap.bundle.min.js').then(() => {
        const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]')
        const tooltipList = [...tooltipTriggerList].map(tooltipTriggerEl => new bootstrap.Tooltip(tooltipTriggerEl))
      })
    })

    const toggleStudentFilter = (student) => {
      selectedStudent.value = selectedStudent.value === student.id ? null : student.id;
      if (selectedStudent.value) {
        searchQuery.value = '';
      }
    }

    const handleSearch = () => {
      if (searchQuery.value) {
        selectedStudent.value = null;
      }
    }

    const handleAcceptedChange = () => {
      if (selectedActivity.value.accepted) {
        selectedActivity.value.teacherGrade = selectedActivity.value.grade;
      }
    }

    const saveAndCloseModal = () => {
      if (selectedActivity.value) {
        const studentIndex = students.value.findIndex(s => s.name === selectedActivity.value.studentName);
        const activityIndex = selectedActivity.value.enigmaNumber - 1;

        if (studentIndex !== -1) {
          const isSecondTheme = activityIndex >= 12;
          const activities = isSecondTheme ? 'activities2' : 'activities';
          const adjustedIndex = isSecondTheme ? activityIndex - 12 : activityIndex;

          const finalGrade = selectedActivity.value.accepted ? 
            selectedActivity.value.grade : 
            selectedActivity.value.teacherGrade;

          const newStatus = (selectedActivity.value.teacherGrade !== '' && !isNaN(selectedActivity.value.teacherGrade)) ? 
            'teacherEvaluated' : 
            students.value[studentIndex][activities][adjustedIndex].status;

          students.value[studentIndex][activities][adjustedIndex] = {
            ...students.value[studentIndex][activities][adjustedIndex],
            status: newStatus,
            grade: finalGrade,
            comments: selectedActivity.value.comments
          };
        }
      }

      const modalElement = document.getElementById('evaluationModal');
      if (modalElement._bsModal) {
        modalElement._bsModal.hide();
      }
    }

    const filteredStudents = computed(() => {
      let result = students.value;

      if (selectedStudent.value) {
        result = result.filter(student => student.id === selectedStudent.value);
      } else if (searchQuery.value) {
        const query = searchQuery.value.toLowerCase();
        result = result.filter(student => 
          student.name.toLowerCase().includes(query)
        );
      }

      return result;
    });

    return {
      students,
      selectedActivity,
      getStatusClass,
      openModal,
      getCellType,
      isExpanded1,
      isExpanded2,
      filteredStudents,
      selectedStudent,
      toggleStudentFilter,
      searchQuery,
      handleSearch,
      isExplicaAlumno1,
      saveAndCloseModal
    }
  }
}
</script>

<style scoped>
.collapsed {
  display: none;
}

.toggle-icon {
  margin-left: 8px;
  font-size: 12px;
}

/* Columnas para el primer tema */
[data-cell-type]:not([data-cell-type="tema"]):nth-child(-n+12) {
  display: v-bind(isExpanded1 ? 'table-cell' : 'none');
}

/* Columnas para el segundo tema */
[data-cell-type]:not([data-cell-type="tema"]):nth-child(n+13) {
  display: v-bind(isExpanded2 ? 'table-cell' : 'none');
}
.fixed-column {
  position: sticky;
  left: 0;
  background: white;
  z-index: 1;
  vertical-align: middle;
  text-align: center;
}

.status-circle {
  display: inline-block;
  width: 14px;
  height: 14px;
  border-radius: 50%;
  margin-left: 8px;
  flex-shrink: 0;
}

.table-responsive {
  max-height: 80vh;
  width: 90%;
  max-width: 90%;
  margin: 0 auto;
  overflow: auto;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

.table thead tr:first-child th {
  position: sticky;
  top: 0;
  z-index: 2;
  background-color: inherit;
}

.table thead tr:last-child th {
  position: sticky;
  top: 42px;
  z-index: 2;
  background-color: inherit;
}

.table thead th.fixed-column {
  z-index: 3;
}

/* Mantener los colores de fondo en las celdas fijas */
[data-column-type="tema"].fixed-column {
  background-color: #0799fe !important;
}
[data-column-type="enigma"].fixed-column {
  background-color: #ffa641 !important;
}
[data-column-type="esquema"].fixed-column {
  background-color: #63038d !important;
}
[data-column-type="explica"].fixed-column {
  background-color: #009742 !important;
}
[data-column-type="coding"].fixed-column {
  background-color: #cbc200 !important;
}

@media (max-width: 991px) {
  .legend-container {
    width: 90%;
    max-width: 90%;
    margin: 20px auto 0;
  }
  .d-flex.align-items-start.flex-column.flex-lg-row {
    align-items: center !important;
  }
}

.table {
  margin-bottom: 0;
  width: 100%;
  font-family: 'Titillium Web', sans-serif;
  font-weight: bold;
}

.table th,
.table td {
  text-align: center;
  vertical-align: middle;
  white-space: nowrap;
}

/* Colores para encabezados por tipo */
[data-column-type="tema"] {
  background-color: #0799fe !important;
  color: white !important;
}

[data-column-type="enigma"] {
  background-color: #ffa641 !important;
  color: white !important;
}

[data-column-type="esquema"] {
  background-color: #63038d !important;
  color: white !important;
}

[data-column-type="explica"] {
  background-color: #009742 !important;
  color: white !important;
}

[data-column-type="coding"] {
  background-color: #cbc200 !important;
  color: white !important;
}

/* Colores para celdas del cuerpo por tipo */
[data-cell-type="tema"] {
  background-color: #0799fe !important;
  color: white !important;
}

[data-cell-type="enigma"] {
  background-color: #ffeccc !important;
}

[data-cell-type="esquema"] {
  background-color: #f9eeff !important;
}

[data-cell-type="explica"] {
  background-color: #edffeb !important;
}

[data-cell-type="coding"] {
  background-color: #ffffec !important;
}

.table tbody tr:hover td {
  background-color: rgba(0, 0, 0, 0.1) !important;
}

.table tbody tr:hover td.fixed-column {
  background-color: rgba(0, 77, 152, 0.15) !important;
}

.activity-cell:active {
  background-color: rgba(0, 77, 152, 0.2);
}

.legend-container {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  font-size: 13px;
  width: 100%;
}

@media (min-width: 992px) {
  .legend-container {
    width: auto;
    min-width: 250px;
  }
}

.legend-item {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.legend-item .status-circle {
  width: 12px;
  height: 12px;
}

.table thead .fixed-column {
  background-color: #3b56a1 !important;
  color: white;
}

.table thead tr:first-child .fixed-column {
  background-color: #3b56a1 !important;
  top: 0;
  z-index: 4;
}

.table thead tr:last-child .fixed-column {
  background-color: #3b56a1 !important;
  top: 42px;
  z-index: 4;
}

.selected-student {
  background-color: #e3f2fd !important;
  font-weight: bold;
}

.fixed-column:hover {
  background-color: #f5f5f5;
}
</style>