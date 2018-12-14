<template>
  <div @click="clickHandler" class="big-card-wrapper">
    <p> {{params.title}} big </p>
    <p> {{params.timer}} big </p>
  </div>
</template>

<script>
export default {
  props: ['params'],
  methods: {
    clickHandler (ev) {
      this.$emit('clicked', ev)
    }
  }
}
</script>

<style>
  .big-card-wrapper {
    width:100%;
    height:100%;
    top:0;
    left:0;
    position:absolute;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    background-color:red;
    color:white;
    transition:all 2s ease
  }
</style>
