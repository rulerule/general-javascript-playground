<template>
  <div @scroll="scrollHandler" class="home">
    <app-header :scrolled="scrolled" :backHandler="backStep"></app-header>
    <app-breadcrumbs :scrolled="scrolled" :steps="steps" :activeStep="activeStep"></app-breadcrumbs>
    <div class="filler">
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
      <h1>FILLER TEXT</h1>
    </div>
    <button @click="advanceStep" >Advance Step</button>
  </div>
</template>

<script>
import Breadcrumbs from '@/components/Breadcrumbs'
import { breadcrumbsCreate } from '@/assets/auxObjects/breadcrumbsAccountCreat'
import StepsHeader from '@/components/StepsHeader'
export default {
  data () {
    return {
      activeStep: 1,
      steps: breadcrumbsCreate.steps,
      scrolled: 0
    }
  },
  components: {
    'app-breadcrumbs': Breadcrumbs,
    'app-header': StepsHeader
  },
  methods: {
    advanceStep () {
      if (this.activeStep === this.steps.length) return
      this.activeStep++
    },
    backStep () {
      if (this.activeStep === 1) return
      --this.activeStep
    },
    scrollHandler (event) {
      this.scrolled = event.target.scrollTop
    }
  }
}
</script>

<style lang="scss">
.home {
  height:100%;
  width:100%;
  box-sizing:border-box;
  overflow:auto;
  .filler {
    height:1600px;
  }
}
</style>
