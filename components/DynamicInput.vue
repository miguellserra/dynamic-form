<template>
  <div class="field">
    <label>{{ props.name }}:</label>
    <input :type="props.type === 'int' ? 'number' : props.type" />
  </div>
</template>

<script setup lang="ts">
const props = defineProps(["name", "type"]);
</script>

<style>
.field {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

label {
  font-size: 1.02em;
  margin-bottom: 0.5rem;
  margin-left: 0.15rem;
}

input {
  padding: 0.5rem 1rem;
  border-radius: 5px;
  border: 1px solid #8d8d8d;
  min-width: 200px;
}
</style>
