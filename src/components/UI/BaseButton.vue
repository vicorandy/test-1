<template>
  <button :class="mode">
    <slot></slot>
  </button>
</template>
<style scoped></style>
<script>
export default {
  props: ['mode'],
};
</script>
<style scoped>
button {
  background-color: #3a0061;
  border: 1px solid #3a0061;
  color: white;
  padding: 0.74rem 1.5rem;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #270041;
  border-block-color: #270041;
}

.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}
.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>
