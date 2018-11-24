<template>
  <div :class="{fixing: positionFixed}" class="breadcrumbs-wrapper">
    <div class="breadcrumbs-container">
      <div
        :class="{active: activeStep == breadcrumb.position}"
        v-for="breadcrumb in steps"
        :key="breadcrumb.position"
        class="breadcrumb"
      >
        <div class="numberInfo">{{breadcrumb.position}}</div>
      </div>
    </div>
    <div class="description">{{steps[activeStep -1].description}}</div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      positionFixed: false
    }
  },
  props: {
    steps: Array,
    activeStep: Number,
    scrolled: Number
  },
  watch: {
    scrolled (newVal, oldVal) {
      if (newVal >= 72) {
        this.positionFixed = true
      } else {
        this.positionFixed = false
      }
    }
  }
}
</script>

<style lang="scss">
.breadcrumbs-wrapper {
  width:100%;
  height:90px;
  display:flex;
  flex-direction:column;
  margin-bottom:40px;
  box-sizing:border-box;
  padding-left:15px;
  padding-right:15px;
  padding-top:35px;
  background-color:white;
  .breadcrumbs-container {
    margin-bottom: 22px;
    display:flex;
    flex-direction:row;
    justify-content:space-between;
    background-color:white;
    .breadcrumb {
      position:relative;
      height:1px;
      min-width:40px;
      width:15%;
      background-color:#d8d8d8;
      .numberInfo {
        position:absolute;
        bottom:10px;
        left:50%;
        transform:translateX(-50%);
        color:#ffb413;
        display:none;
      }
      &.active {
        height:3px;
        background-color:#ffb413;
        .numberInfo {
          display:block;
        }
      }
    }
  }
  .description {
    font-size:13px;
    color:#ffb413;
    align-self:flex-start;
    text-transform: uppercase;
    margin-bottom:10px;
  }
  &.fixing {
    position:fixed;
    top:73px;
    left:0;
    border-bottom:2px solid #d8d8d8;
    z-index:10;
    margin-bottom:0;
  }
}
</style>
