<template>
  <div>
    <span>{{ name }}</span>
    <input
      type="text"
      :value="variable"
      @input="$emit('input', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  props: {
    variable: Number,
    name: String,
  },
};
</script>

<style>
</style>