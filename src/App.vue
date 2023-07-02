<template>
  <div class="container mt-5">
    <div>
      <h1 class="title">
        Kanban Board
      </h1>
    </div>

    <!-- Add Task -->
    <div class="row">
      <div class="col form-inline">
        <b-form-input v-model="newTask" placeholder="Enter Task" @key.enter="add"></b-form-input>
        <b-button class="ml-2" variant="primary" @click="add">
          Add
        </b-button>
      </div>
    </div>

    <!-- Backlog Category -->
    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert alert-secondary">
          <h3>Backlog</h3>
          <draggable class="list-group kanban-column" :list="arrBacklog" group="tasks">
            <div class="list-group-item" v-for="element in arrBacklog" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <!-- In progress Category -->
      <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>In Progress</h3>
          <draggable class="list-group kanban-column" :list="arrInProgress" group="tasks">
            <div class="list-group-item" v-for="element in arrInProgress" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <!-- Tested Category -->
      <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>Tested</h3>
          <draggable class="list-group kanban-column" :list="arrTested" group="tasks">
            <div class="list-group-item" v-for="element in arrTested" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <!-- Done Category -->
      <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Done</h3>
          <draggable class="list-group kanban-column" :list="arrDone" group="tasks">
            <div class="list-group-item" v-for="element in arrDone" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: 'App',
  components: {
    draggable
  },
  // Predefined Tasks
  data() {
    return {
      newTask: "",
      // Buckets
      arrBacklog: [
        { name: "Code Sign Up Page" },
        { name: "Test Dashboard" },
        { name: "Style Registration" },
        { name: "Help with Designs" },
      ],
      // Categories 
      arrInProgress: [],
      arrTested: [],
      arrDone: [],
    }
  },
  methods: {
    // Add new task
    add() {
      if (this.newTask) {
        this.arrBacklog.push({ name: this.newTask });
        this.newTask = "";
      }
    }
  }
}
</script>

<style>
.kanban-column {
  min-height: 300px;
}

.title {
  margin-bottom: 30px;
}
</style>


