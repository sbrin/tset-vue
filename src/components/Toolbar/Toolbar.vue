<template lang="pug">
div
  ToolbarDrilling
  ToolbarTolerance
  ToolbarSurfacefinish
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import ToolbarDrilling from '@/components/Toolbar/ToolbarDrilling.vue';
import ToolbarTolerance from '@/components/Toolbar/ToolbarTolerance.vue';
import ToolbarSurfacefinish from '@/components/Toolbar/ToolbarSurfacefinish.vue';

@Component({
  components: {
    ToolbarDrilling,
    ToolbarTolerance,
    ToolbarSurfacefinish,
  },
})
export default class Toolbar extends Vue {}
</script>

<style lang="sass">
.tooblar-prop
  cursor: move
</style>
