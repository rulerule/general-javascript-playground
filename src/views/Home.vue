<template>
  <section class="home-wrapper">
    <app-card-container :params="card" v-for="card in cards" :key="card.id"></app-card-container>
  </section>
</template>

<script>
import { cards } from '@/assets/cards.js'
import CardContainer from '@/components/CardContainer.vue'
export default {
  name: 'home',
  data () {
    return {
      cards: cards.list
    }
  },
  components: {
    'app-card-container': CardContainer
  }
}
</script>

<style lang="scss">
.home-wrapper {
  width:100%;
  height:100%;
  background-color:black;
  display:flex;
  flex-direction:row;
  flex-flow:wrap;
  justify-content:center;
  align-items:center;
  overflow:auto;
  box-sizing:border-box;
  padding:25px;
  position:relative;
}
</style>
