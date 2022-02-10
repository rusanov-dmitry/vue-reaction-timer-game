<template>
  <div v-if="score < 300" class="result">
    <h2>Supa fast!</h2>
    <slot></slot>
  </div>
  <div v-else-if="score < 500" class="result">
    <h2>Okayge</h2>
    <slot></slot>
  </div>
  <div v-else class="result">
    <h2>Supa slow...</h2>
    <slot></slot>
  </div>
  <p>Click play to test your reaction again!</p>
</template>

<script>
export default {
  props: ['score']
}
</script>

<style>
.result {
  margin-top: 60px;
}
.result h2 {
  color: #0faf87;
}
.result p {
  font-size: 18px;
}
.result p span {
  font-weight: 800;
}
</style>