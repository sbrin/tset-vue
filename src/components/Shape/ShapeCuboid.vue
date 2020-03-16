<template lang="pug">
.shape-cuboid
  div
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_top
  div

  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_left
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_center
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_right

  div
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_bottom-center
  div

  div
  BaseSurface.shape-cuboid__edge.shape-cuboid__edge_bottom
  div
</template>

<script lang="ts">
import { Component } from 'vue-property-decorator';
import Shape from '@/components/Shape/Shape.vue';
import BaseSurface from '@/components/Shape/BaseSurface.vue';

@Component({
  components: {
    BaseSurface,
  },
})
export default class ShapeCuboid extends Shape {}
</script>

<style scoped lang="sass">
.shape-highlighted
  background: lightblue
  height: 100%
.shape-cuboid
  display: grid
  grid-template-columns: 1fr 1fr 1fr

  &__edge
    box-sizing: border-box
    height: 150px
    border: 2px solid black
    &_top
      border-bottom: 1px
    &_left
      border-right: 1px
    &_center
    &_right
      border-left: 1px
    &_bottom-center
      border-top: 1px
    &_bottom
      border-top: 1px
</style>
