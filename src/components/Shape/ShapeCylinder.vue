<template lang="pug">
.shape-cuboid
  div
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_top
  div

  div
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_center
  div

  div
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_top
  div
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import BaseSurface from '@/components/Shape/BaseSurface.vue';

@Component({
  components: {
    BaseSurface,
  },
})
export default class ShapeCylinder extends Vue {}
</script>

<style scoped lang="sass">
.shape-highlighted
  background: lightblue
  height: 100%
.shape-cuboid
  display: grid
  grid-template-columns: 1fr 2fr 1fr
  justify-items: center

  &__edge
    box-sizing: border-box
    border: 2px solid black
    &_top
      border-radius: 50%
      height: 200px
      width: 200px
    &_center
      width: calc(3.14 * 200px)
      height: 200px
</style>
