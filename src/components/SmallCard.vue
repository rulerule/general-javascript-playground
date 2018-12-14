<template>
  <div @click="clickHandler" class="small-card-wrapper">
    <p> {{params.title}} small </p>
    <p> {{params.timer}} small </p>
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

<style lang="scss">
.small-card-wrapper {
  width:100%;
  height:100%;
  color:white;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  p {
    pointer-events:none;
  }
  h1 {
    pointer-events:none;
  }
}
</style>
