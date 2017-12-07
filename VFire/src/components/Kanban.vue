<template>
  <div>
    <div>
    <div class="card mb-3" style="color:black; text-align:left; max-width: 20rem;">
    <div class="card-header">Header</div>
    <div class="card-body text-primary">
      <h4 style="color:black;" class="card-title">Primary card title</h4>
      <p style="color:black;" class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
      <button data-toggle="modal" data-target="#detailTask" type="button" class="btn btn-secondary btn-sm">detail</button>
    </div>
  </div>
  </div>
  <!-- START MODAL -->
    <div class="modal fade" id="detailTask" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">New message</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <form>
              <div class="form-group">
                <label for="recipient-name" class="col-form-label">Recipient:</label>
                <input type="text" class="form-control" id="recipient-name">
              </div>
              <div class="form-group">
                <label for="message-text" class="col-form-label">Message:</label>
                <textarea class="form-control" id="message-text"></textarea>
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary">Send message</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Kanban'
}
</script>

<style>

</style>
