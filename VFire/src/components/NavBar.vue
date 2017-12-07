<template>
  <div >
    <nav class="navbar navbar-expand-lg navbar-primary bg-primary">
    <div class="container">
      <a style="color:white; font-weight:bold;" class="navbar-brand" href="#">Kanban Board</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarColor02" aria-controls="navbarColor02" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
    </div>

    <div class="collapse navbar-collapse" id="navbarColor02">
      <ul class="navbar-nav mr-auto">
      </ul>
      <form class="form-inline my-2 my-lg-0">
        <button data-toggle="modal" data-target="#modalAddTask" class="btn btn-outline-light my-2 my-sm-0" type="submit">Add Task</button>
      </form>
    </div>
  </nav>
  </div>
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style scoped>

</style>
