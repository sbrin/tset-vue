<template lang="pug">
b-form-group(
  label-for="select_shape"
  label="Select shape"
)
  b-form-select(
    id="select_shape"
    :options="options"
    v-model="selected"
    @input="selectShape"
  )
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class SelectShape extends Vue {
  selected = '';

  options: Array<string> = ['cuboid', 'cylinder'];

  selectShape(e: string) {
    this.$root.$emit('SelectShape', e);
  }
}
</script>
