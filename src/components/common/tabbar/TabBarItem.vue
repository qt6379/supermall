<template>
  <div class="tab_bar_item" @click="divClick">
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
  export default {
    name: "TabBarItem",
    props: {
      path: String,
      textColor:{
        type: String,
        default: 'red'
      },
    },
    data() {
      return {

      }
    },
    computed: {
      isActive() {
        return this.$route.path.indexOf(this.path) !== -1
      },
      activeStyle() {
        return this.isActive ? {color: this.textColor} : {}
      }
    },
    methods: {
      divClick() {
        this.$router.replace(this.path)
      }
    }
  }
</script>

<style scoped>
  .tab_bar_item{
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }
  .tab_bar_item img{
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;
  }

</style>
