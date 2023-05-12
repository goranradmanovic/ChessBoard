<script setup>
  defineProps({
    chessmoves: {
      type: Array,
      required: true,
      default: []
    }
  })
</script>

<template>
  <div class="sidebar mt-5">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">Side Bar</h5>
        <h6 class="card-subtitle mb-2 text-muted">All chess game moves</h6>
        <p class="card-text">
          <ul class="list-group">
            <li v-for="(item, index) in chessmoves" :key="index" class="list-group-item text-capitalize">Move {{ index + 1 }}. ({{ item }})</li>
          </ul>
        </p>
      </div>
    </div>
  </div>
</template>
