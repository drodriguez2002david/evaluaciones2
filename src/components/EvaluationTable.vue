
<template>
  <div class="container-fluid h-100 d-flex align-items-center justify-content-center">
    <div class="table-responsive">
      <table class="table table-bordered">
        <thead>
          <tr>
            <th class="fixed-column">ALUMNOS</th>
            <th>TEMA</th>
            <th colspan="2">ACERTIJO</th>
            <th>ESQUEMA</th>
            <th colspan="2">EXPLICA EL ALUMNO</th>
            <th colspan="5">CODING</th>
          </tr>
          <tr>
            <th class="fixed-column"></th>
            <th>EL CICLO DEL AGUA</th>
            <th>Acertijo 1</th>
            <th>Acertijo 2</th>
            <th>Esquema 1</th>
            <th>Explica 1</th>
            <th>Explica 2</th>
            <th>Coding 1</th>
            <th>Coding 2</th>
            <th>Coding 3</th>
            <th>Coding 4</th>
            <th>Coding 5</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="student in students" :key="student.id">
            <td class="fixed-column">{{ student.name }}</td>
            <td></td>
            <td v-for="(activity, index) in student.activities" :key="index" @click="openModal(student, activity)">
              {{ activity.grade || '-' }}
              <span :class="['status-circle', getStatusClass(activity.status)]"></span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Modal -->
    <div class="modal fade" id="evaluationModal" tabindex="-1">
      <div class="modal-dialog modal-lg">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Evaluación</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
          </div>
          <div class="modal-body" v-if="selectedActivity">
            <iframe :src="selectedActivity.chatUrl" class="w-100" style="height: 400px;"></iframe>
            <div class="mt-3">
              <div class="mb-3" v-if="selectedActivity.status === 'aiEvaluated'">
                <label class="form-label">Nota AIDIN</label>
                <div class="input-group">
                  <input type="number" class="form-control" v-model="selectedActivity.grade" readonly>
                  <div class="input-group-text">
                    <input type="checkbox" v-model="selectedActivity.accepted">
                  </div>
                </div>
              </div>
              <div class="mb-3">
                <label class="form-label">Nota del profesor</label>
                <input type="number" class="form-control" v-model="selectedActivity.teacherGrade">
              </div>
              <div class="mb-3">
                <label class="form-label">Comentarios</label>
                <textarea class="form-control" v-model="selectedActivity.comments"></textarea>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import 'bootstrap'

export default {
  name: 'EvaluationTable',
  setup() {
    const students = ref([
      { id: 1, name: 'Ana García', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 2, name: 'Carlos Rodríguez', activities: Array(10).fill({ status: 'pending', chatUrl: '' }) },
      { id: 3, name: 'María López', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 4, name: 'Juan Martínez', activities: Array(10).fill({ status: 'submitted', chatUrl: '' }) },
      { id: 5, name: 'Laura Sánchez', activities: Array(10).fill({ status: 'aiEvaluated', grade: 8, chatUrl: '' }) },
      { id: 6, name: 'David Fernández', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 7, name: 'Sofia Pérez', activities: Array(10).fill({ status: 'pending', chatUrl: '' }) },
      { id: 8, name: 'Pablo Gómez', activities: Array(10).fill({ status: 'submitted', chatUrl: '' }) },
      { id: 9, name: 'Elena Torres', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 10, name: 'Miguel Ruiz', activities: Array(10).fill({ status: 'aiEvaluated', grade: 7, chatUrl: '' }) },
      { id: 11, name: 'Carmen Díaz', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 12, name: 'José Moreno', activities: Array(10).fill({ status: 'pending', chatUrl: '' }) },
      { id: 13, name: 'Isabel Jiménez', activities: Array(10).fill({ status: 'submitted', chatUrl: '' }) },
      { id: 14, name: 'Alberto Romero', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 15, name: 'Lucía Navarro', activities: Array(10).fill({ status: 'aiEvaluated', grade: 9, chatUrl: '' }) },
      { id: 16, name: 'Roberto Muñoz', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 17, name: 'Patricia Álvarez', activities: Array(10).fill({ status: 'pending', chatUrl: '' }) },
      { id: 18, name: 'Fernando Castro', activities: Array(10).fill({ status: 'submitted', chatUrl: '' }) },
      { id: 19, name: 'Cristina Ortiz', activities: Array(10).fill({ status: 'notStarted', chatUrl: '' }) },
      { id: 20, name: 'Andrés Delgado', activities: Array(10).fill({ status: 'aiEvaluated', grade: 8, chatUrl: '' }) }
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

    const openModal = (student, activity) => {
      selectedActivity.value = activity
      const modal = new bootstrap.Modal(document.getElementById('evaluationModal'))
      modal.show()
    }

    return {
      students,
      selectedActivity,
      getStatusClass,
      openModal
    }
  }
}
</script>

<style scoped>
.fixed-column {
  position: sticky;
  left: 0;
  background: white;
  z-index: 1;
}

.status-circle {
  display: inline-block;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  margin-left: 5px;
}

.table-responsive {
  max-height: 80vh;
  width: 95%;
  max-width: 1400px;
  margin: 0 auto;
  overflow: auto;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

.table {
  margin-bottom: 0;
  width: 100%;
}
</style>
