<script>
export default {
  props: {
    task: Object,
    idx: Number
  },
  emits: ['removeTask']
}
</script>

<template>
  <div class="card mb-2" style="width: 18rem;">
    <div class="card-body">
      <h5 class="card-title">Deadline: {{ task.deadline }}</h5>
      <hr>
      <p class="card-text">{{ task.desc }}</p>
      <button class="btn btn-success" @click="$emit('removeTask', idx)">Done</button>
    </div>
  </div>
</template>

