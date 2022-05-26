<script setup lang="ts">
defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="container">
    <div class="backdrop">
      <div class="highlights">
        <!-- cloned text with <mark> tags here -->
      </div>
    </div>
    <textarea>
    <!-- user input here -->
    </textarea>
  </div>
</template>

<style scoped>
  @import 'src/test.css';
</style>
