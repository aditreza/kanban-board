<template>
  <div style="margin-top:5%; margin-bottom:5%;" class="container">
      <div class="row">
        <!-- START BACK-LOG -->
        <div class="col">
          <div class="card border-danger mb-3" style="max-width: 20rem;">
            <div style="font-weight:bold; background:#dc3545; color:white" class="card-header">BACK-LOG</div>
            <div v-for="kanbanTasks of task" :key="kanbanTasks['.key']" class="card-body text-primary">
              <div v-if="kanbanTasks.status == 'backlog'">
                <!-- start kanban -->
                <div class="kanban-card card mb-3" style="margin-bottom: -28%; margin-bottom:-28%; color:black; text-align:left; max-width: 20rem;">
                  <div class="card-header">{{ kanbanTasks.title }}</div>
                  <div class="card-body text-primary">
                    <p style="color:black;" class="card-text">{{ kanbanTasks.point }}</p>
                    <p style="color:black;" class="card-text">{{ kanbanTasks.toAssign }}</p>
                    <button @click="toremove(kanbanTasks['.key'])" type="button" class="btn btn-danger btn-sm">delete</button>
                    <button @click="toTodo(kanbanTasks['.key'])" type="button" class="btn btn-warning btn-sm">TO-DO</button>
                  </div>
                </div>
                <!-- end kanban -->
              </div>
            </div>
          </div>
        </div>
        <!-- START TO-DO -->
        <div class="col">
          <div class="card border-warning mb-3" style="max-width: 20rem;">
            <div style="font-weight:bold; background:#fec207; color:white" class="card-header">TO-DO</div>
            <div v-for="kanbanTasks of task" :key="kanbanTasks['.key']" class="card-body text-primary">
              <div v-if="kanbanTasks.status == 'todo'">
                <!-- start kanban -->
                <div class="card mb-3" style="color:black; text-align:left; max-width: 20rem;">
                  <div class="card-header">{{ kanbanTasks.title }}</div>
                  <div class="card-body text-primary">
                    <p style="color:black;" class="card-text">{{ kanbanTasks.point }}</p>
                    <p style="color:black;" class="card-text">{{ kanbanTasks.toAssign }}</p>
                    <button @click="toBacklog(kanbanTasks['.key'])" type="button" class="btn btn-danger btn-sm">Back-log</button>
                    <button @click="toremove(kanbanTasks['.key'])"type="button" class="btn btn-warning btn-sm">delete</button>
                    <button @click="toDoing(kanbanTasks['.key'])" type="button" class="btn btn-primary btn-sm">Doing</button>
                  </div>
                </div>
                <!-- end kanban -->
              </div>
            </div>
          </div>
        </div>
        <!-- START DOING -->
        <div class="col">
          <div class="card border-primary mb-3" style="max-width: 20rem;">
            <div style="font-weight:bold; background:#027aff; color:white" class="card-header">DOING</div>
            <div v-for="kanbanTasks of task" :key="kanbanTasks['.key']" class="card-body text-primary">
              <div v-if="kanbanTasks.status == 'doing'">
               <!-- start kanban -->
                <div class="card mb-3" style="color:black; text-align:left; max-width: 20rem;">
                  <div class="card-header">{{ kanbanTasks.title }}</div>
                  <div class="card-body text-primary">
                    <p style="color:black;" class="card-text">{{ kanbanTasks.point }}</p>
                    <p style="color:black;" class="card-text">{{ kanbanTasks.toAssign }}</p>
                    <button @click="toTodo(kanbanTasks['.key'])" type="button" class="btn btn-warning btn-sm">To-Do</button>
                    <button @click="toremove(kanbanTasks['.key'])" type="button" class="btn btn-primary btn-sm">delete</button>
                    <button @click="toDone(kanbanTasks['.key'])" type="button" class="btn btn-success btn-sm">Done</button>
                  </div>
                </div>
                <!-- end kanban -->
              </div>
            </div>
          </div>
        </div>
        <!-- START DONE -->
        <div class="col">
          <div class="card border-success mb-3" style="max-width: 20rem;">
            <div style="font-weight:bold; background:#26a745; color:white" class="card-header">DONE</div>
            <div v-for="kanbanTasks of task" :key="kanbanTasks['.key']" class="card-body text-primary">
              <div v-if="kanbanTasks.status == 'done'">
                <!-- start kanban -->
                <div class="card mb-3" style="color:black; text-align:left; max-width: 20rem;">
                  <div class="card-header">{{ kanbanTasks.title }}</div>
                  <div class="card-body text-primary">
                    <p style="color:black;" class="card-text">{{ kanbanTasks.point }}</p>
                    <p style="color:black;" class="card-text">{{ kanbanTasks.toAssign }}</p>
                    <button @click="toDoing(kanbanTasks['.key'])" type="button" class="btn btn-primary btn-sm">Doing</button>
                    <button @click="toremove(kanbanTasks['.key'])" type="button" class="btn btn-success btn-sm">delete</button>
                  </div>
                </div>
                <!-- end kanban -->
              </div>
            </div>
          </div>
        </div>
        
      </div>
    <!-- start modal new task-->
    <div class="modal fade" id="modalAddTask" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Add New Task</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form>
              <div style="text-align:left;" class="form-group">
                <label for="recipient-name" class="col-form-label">Title:</label>
                <input v-model="taskTraffic.title" type="text" class="form-control" required>
                <label for="recipient-name" class="col-form-label">Desc:</label>
                <textarea v-model="taskTraffic.desc" type="text" class="form-control" required></textarea>
                <label for="recipient-name" class="col-form-label">Point:</label>
                <input v-model="taskTraffic.point" type="number" placeholder="0" class="form-control" required>
                <label for="recipient-name" class="col-form-label">Assign:</label>
                <input v-model="taskTraffic.toAssign" type="text" class="form-control" required>
                <label for="recipient-name" class="col-form-label">Status:</label>
                <input v-model="taskTraffic.status" type="text" class="form-control" disabled>
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
            <button @click="submitTask(taskTraffic)" data-dismiss="modal" type="button" class="btn btn-primary">Send message</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Kanban from '@/components/Kanban'
import * as firebase from 'firebase'

const app = firebase.initializeApp({
  databaseURL: 'https://kanban-board-9ec4a.firebaseio.com',
  projectId: 'kanban-board-9ec4a'
})

const db = app.database()
const kanbanTasks = db.ref('tasks')
export default {
  name: 'KanbanBoard',
  firebase: {
    task: kanbanTasks
  },
  components: {
    Kanban
  },
  data () {
    return {
      taskTraffic: {
        title: '',
        desc: '',
        point: '',
        toAssign: '',
        status: 'backlog'
      }
    }
  },
  methods: {
    submitTask (data) {
      console.log(data)
      kanbanTasks.push(data)
      this.taskTraffic.title = ''
      this.taskTraffic.desc = ''
      this.taskTraffic.point = ''
      this.taskTraffic.toAssign = ''
    },
    toTodo (key) {
      console.log('masuk')
      kanbanTasks.child(key).update({ status: 'todo' })
    },
    toBacklog (key) {
      kanbanTasks.child(key).update({ status: 'backlog' })
    },
    toDoing (key) {
      kanbanTasks.child(key).update({ status: 'doing' })
    },
    toDone (key) {
      kanbanTasks.child(key).update({ status: 'done' })
    },
    toremove (key) {
      kanbanTasks.child(key).remove()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
