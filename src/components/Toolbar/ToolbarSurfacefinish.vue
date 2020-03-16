<template lang="pug">
div
  h5 {{ proptype }}
  b-form-group
    label.tooblar-prop(
      for="toolbar_input_finish"
      draggable="true"
      @dragstart="dragStart"
      @dragend="dragEnd"
    ) Finish
    b-form-row
      b-col
        b-form-input(
          id="toolbar_input_finish"
          type="number"
          v-model="value"
        )
      b-col
        b-form-select(
          id="toolbar_input_finish_unit"
          :options="['nm', 'μm', 'mm']"
          v-model="unit"
        )
</template>

<script lang="ts">
import { Component } from 'vue-property-decorator';
import BaseToolbar from './BaseToolbar.vue';

@Component
export default class ToolbarSurfacefinish extends BaseToolbar {
  name = 'finish';

  proptype = 'Surfacefinish';

  unit = 'mm';

  get propsData() {
    return JSON.stringify({
      type: this.proptype,
      name: this.name,
      value: this.value,
      unit: this.unit,
    });
  }
}
</script>

<style scoped lang="sass"></style>
