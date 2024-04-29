<template>
    <button :class="mode">
        <slot></slot>
    </button>
</template>

<script>
export default {
  props:["mode"]
}
</script>

<style scoped>

button {
  
  padding: 0.75rem 1.5rem;  
  margin-left: 5px;
  background-color: rgb(6, 6, 97);
  border: 1px solid rgb(6, 6, 97);
  border-radius: 10%;
  color: white;
  font-size: 1rem;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: rgb(16, 16, 132);
  border-color: rgb(16, 16, 132);
}

.flat {
  background-color: rgb(148, 163, 165);
  border: none; 
  
}

.flat:hover,
.flat:active {
  background-color: rgb(171, 188, 190);
}

</style>