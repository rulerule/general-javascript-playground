<template>
  <div class="container card-wrapper col-sm-5 col-md-3">
    <small-card @clicked="smallCardClickHandler" :params="params"></small-card>
    <transition
    mode="out-in"
    @beforeEnter="beforeEnter"
    @enter="enter"
    @leave="leave">
      <big-card :params="params" v-if="bigActive" @clicked="bigCardClickHandler"></big-card>
    </transition>
  </div>
</template>

<script>
import BigCard from '@/components/BigCard.vue'
import SmallCard from '@/components/SmallCard.vue'
import velocity from 'velocity-animate'
export default {
  name: 'card',
  props: {
    params: {
      title: String,
      timer: Number
    }
  },
  data () {
    return {
      bigActive: false
    }
  },
  components: {
    'small-card': SmallCard,
    'big-card': BigCard
  },
  methods: {
    smallCardClickHandler (ev) {
      this.smallCardWidth = `${ev.target.clientWidth}px`
      this.smallCardHeight = `${ev.target.clientHeight}px`
      this.smallCardTop = `${ev.target.offsetTop}px`
      this.smallCardLeft = `${ev.target.offsetLeft}px`
      this.bigActive = true
    },
    bigCardClickHandler (ev) {
      let el = ev.target
      velocity(
        el,
        {
          width: this.smallCardWidth,
          height: this.smallCardHeight,
          top: this.smallCardTop,
          left: this.smallCardLeft
        },
        {
          duration: 'fast'
        }
      )
      setTimeout(() => { this.bigActive = false }, 2200)
    },
    beforeEnter (el) {
      el.style.width = this.smallCardWidth
      el.style.height = this.smallCardHeight
      el.style.top = this.smallCardTop
      el.style.left = this.smallCardLeft
    },
    enter (el, done) {
      velocity(el, { width: '100%', height: '100%', top: 0, left: 0 }, { duration: 'fast' })
      velocity(el, { complete: done })
    },
    leave (el, done) {
      done()
    }
  }
}
</script>

<style lang="scss">
.card-wrapper {
  min-height:80px;
  height:40%;
  background-color:red;
  margin-bottom:50px;
  margin-left:2.5%;
  margin-right:2.5%;
  position:unset;
}
</style>
