<template lang="pug">
div
  h5 Drilling
  b-form-group
    label.tooblar-prop(
      for="toolbar_input_drilling"
      draggable="true"
      @dragstart="dragStart"
      @dragend="dragEnd"
    ) Diameter
    b-form-input(
      id="toolbar_input_drilling"
      type="number"
      v-model="value"
    )
</template>

<script lang="ts">
import { Component } from 'vue-property-decorator';
import BaseToolbar from './BaseToolbar.vue';

@Component
export default class ToolbarDrilling extends BaseToolbar {
  name = 'diameter';

  proptype = 'Drilling';
}
</script>
