<template>
  <div style="margin-top:5%; margin-bottom:5%;" class="container">
      <div class="row">
        <div class="col">
          <div class="card text-white bg-primary mb-3" style="max-width: 20rem;">
            <div class="card-header">Header</div>
            <div v-for="kanbanTasks of task" :key="kanbanTasks['.key']">
              <Kanban></Kanban>
            </div>
          </div>
        </div>
        <!-- <div class="col"><Kanban></Kanban></div>
        <div class="col"><Kanban></Kanban></div>
        <div class="col"><Kanban></Kanban></div> -->
      </div>
    <!-- start modal -->
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
              <div class="form-group">
                <label for="recipient-name" class="col-form-label">Title:</label>
                <input v-model="taskTraffic.title" type="text" class="form-control" id="recipient-name">
                <label for="recipient-name" class="col-form-label">Desc:</label>
                <input v-model="taskTraffic.desc" type="text" class="form-control" id="recipient-name">
                <label for="recipient-name" class="col-form-label">Point:</label>
                <input v-model="taskTraffic.point" type="text" class="form-control" id="recipient-name">
                <label for="recipient-name" class="col-form-label">Assign:</label>
                <input v-model="taskTraffic.toAssign" type="text" class="form-control" id="recipient-name">
                <label for="recipient-name" class="col-form-label">Status:</label>
                <input v-model="taskTraffic.status" type="text" class="form-control" id="recipient-name">
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
            <button @click="submitTask(taskTraffic)" type="button" class="btn btn-primary">Send message</button>
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
        title: null,
        desc: null,
        point: null,
        toAssign: null,
        status: null
      }
    }
  },
  methods: {
    submitTask (data) {
      console.log(data)
      kanbanTasks.push(data)
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
