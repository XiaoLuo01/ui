<template>
 <div class="layout" :class="layoutClass">
     <slot></slot>
 </div>
</template>

<script>
export default {
    name: 'VioLayout',
 data() {
  return {
      layoutClass: {
          hasSider: false
      }
  }
 },
 components: {

 },
 mounted() {
     this.$children.forEach((vm) => {
        if(vm.$options.name === 'VioSider') {
            this.layoutClass.hasSider = true
        }
     })
 }
}
</script>

<style scoped lang="scss">
.layout {
    display: flex;
    flex-grow: 1;
    flex-direction: column;
    &.hasSider {
        flex-direction: row;
    }
}
</style>
