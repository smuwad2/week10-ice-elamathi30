<script>
import TaskTracker from './subcomponents/TaskTrackertrail.vue'

export default {
  components: { TaskTracker },
  data() {
    return {
      desc: '',
      deadline: '',
      taskList: []
    }
  },
  methods: {
    add() {
      if (this.desc && this.deadline) {
        this.taskList.push({ desc: this.desc, deadline: this.deadline });
        this.desc = '';
        this.deadline = '';
      }
    },
    deleteTask(idx) {
      this.taskList.splice(idx, 1);
    }
  }
}
</script>

<template>
  <div class="mb-3">
    <label class="form-label">Task</label>
    <input type="text" class="form-control" v-model="desc" placeholder="task">
  </div>
  <div class="mb-3">
    <label class="form-label">Deadline</label>
    <input type="date" class="form-control" v-model="deadline">
  </div>

  <button type="button" @click="add" class="btn btn-primary mb-3">Add New Task</button>
  <hr>

  <!-- Display tasks -->
  <div>
 <TaskTracker
  v-for="(task, idx) in taskList"
  :key="idx"
  :task="task"
  :idx="idx"
  @removeTask="deleteTask"
/>
  </div>
</template>
