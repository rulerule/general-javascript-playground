<template>
  <section class="header-wrapper">
    <div :style="{opacity: baseOpacity}" class="overlay-header">
      <img @click="backHandler" src="../assets/back-white.svg" class="back-arrow"/>
      <div class="title">Criar Conta</div>
    </div>
    <img @click="backHandler" src="../assets/back.svg" class="back-arrow"/>
    <div class="title">Criar Conta</div>
  </section>
</template>

<script>
export default {
  data () {
    return {
      baseOpacity: 0
    }
  },
  props: {
    backHandler: Function,
    scrolled: Number
  },
  watch: {
    scrolled (newVal, oldVal) {
      this.baseOpacity = newVal / 50
    }
  }
}
</script>

<style lang="scss">
  .header-wrapper {
    position:relative;
    width:100%;
    height:145px;
    background-image: url('../assets/img.jpg');
    background-repeat: no-repeat;
    background-size:cover;
    background-position-y:-35px;
    display:flex;
    flex-direction:column;
    box-sizing:border-box;
    padding-left:15px;
    padding-top:40px;
    .back-arrow {
      align-self:flex-start;
      margin-bottom:45px;
    }
    .title {
      align-self:flex-start;
      font-size:22px;
      font-weight:bold;
      color:#1a1919;
    }
    .overlay-header {
      position:fixed;
      top:0;
      left:0;
      width:100%;
      height:74px;
      background-color:#d8232a;
      display:flex;
      flex-direction:row;
      box-sizing:border-box;
      padding-left:10px;
      padding-top:44px;
      transition:opacity 0.1s ease;
      z-index:20;
      .back-arrow {
        margin-right:12px;
      }
      .title {
        color:white;
      }
    }
  }
</style>
