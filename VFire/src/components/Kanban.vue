<template>
  <div>
    <div v-for="taskone in task" :key="taskone['.key']" >
    <div class="card mb-3" style="color:black; text-align:left; max-width: 20rem;">
    <div class="card-header">{{ taskone.title }}</div>
    <div class="card-body text-primary">
      <p style="color:black;" class="card-text">{{ taskone.point }}</p>
      <p style="color:black;" class="card-text">{{ taskone.toAssign }}</p>
      <button data-toggle="modal" data-target="#detailTask" type="button" class="btn btn-secondary btn-sm">detail</button>
    </div>
  </div>
  </div>
  <!-- START MODAL -->
    <div class="modal fade" id="detailTask" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 style="color:black;" class="modal-title" id="exampleModalLabel">DETAIL</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form>
              <div style="text-align:left; color:black;" class="form-group">
                <label style="font-weight:bold; color:black;" class="col-form-label">Task Desc :</label>
                <label style="font-weight:bold; color:black;" class="col-form-label">Enak</label><br>
                <label style="font-weight:bold; color:black;" class="col-form-label">Point :</label>
                <label style="font-weight:bold; color:black;" class="col-form-label">5</label><br>
                <label style="font-weight:bold; color:black;" class="col-form-label">Status :</label>
                <label style="font-weight:bold; color:black;" class="col-form-label">Doing</label>
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">prev</button>
            <button type="button" class="btn btn-primary">delete</button>
            <button type="button" class="btn btn-secondary" data-dismiss="modal">next</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Kanban',
  props: ['task']
}
</script>

<style>

</style>
