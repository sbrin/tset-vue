<template lang="pug">
div
  h5 {{ proptype }}
  b-form-group
    label.tooblar-prop(
      for="toolbar_input_tolerance"
      draggable="true"
      @dragstart="dragStart"
      @dragend="dragEnd"
    ) Tolerance
    b-form-select(
      id="toolbar_input_tolerance"
      :options="['fine', 'medium', 'rough']"
      v-model="value"
    )
</template>

<script lang="ts">
import { Component } from 'vue-property-decorator';
import BaseToolbar from './BaseToolbar.vue';

@Component
export default class ToolbarTolerance extends BaseToolbar {
  name = 'tolerance';

  proptype = 'Tolerance';
}
</script>

<style scoped lang="sass"></style>
