<template lang="pug">
div(
  @drop="drop"
  @dragover="allowDrop"
  :class="{'shape-highlighted': highlight}"
)
  div(
    :id="$vnode.tag + _uid"
  )
    b-badge(
        v-for="prop in properties"
        :key="prop.name"
        :variant="prop.value ? 'success': 'warning'"
    ) {{ prop.name }}
  b-popover(
    :target="$vnode.tag + _uid"
    triggers="click"
    :show.sync="popup"
  )
    b-form-group(
      v-for="prop in properties"
      :key="prop.name"
    )
      label.tooblar-prop(
        :for="`toolbar_input_${prop.name}`"
      ) {{ prop.type }}
      b-form-row
        b-col(
          v-if="prop.name !== 'tolerance'"
        )
          b-form-input(
            id="`toolbar_input_${prop.name}`"
            type="number"
            v-model="prop.value"
          )
        b-col(
          v-else-if="prop.name === 'tolerance'"
        )
          b-form-select(
            id="`toolbar_input_${prop.name}`"
            :options="['fine', 'medium', 'rough']"
            v-model="prop.value"
          )
        b-col(v-if="prop.unit")
          b-form-select(
            :options="['nm', 'μm', 'mm']"
            v-model="prop.unit"
          )
        b-col(
          @click="properties = properties.filter(item => item.name !== prop.name)"
        )
          b-btn ×
</template>
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

interface Property {
  name: string;
  value: string;
}

@Component
export default class BaseSurface extends Vue {
  properties: Array<Property> = [];

  popup = false;

  highlight = false;

  drop(e: DragEvent) {
    if (e.dataTransfer) {
      const data = JSON.parse(e.dataTransfer.getData('text'));

      if (!this.properties.find((item) => item.name === data.name)) {
        this.properties.push(data);
      }
    }
  }

  allowDrop(e: DragEvent) {
    e.preventDefault();
  }

  created() {
    this.$root.$on('hidePopups', () => {
      this.popup = false;
    });

    this.$root.$on('dragStart', (name: string) => {
      if (!this.properties.find((item) => item.name === name)) {
        this.highlight = true;
      }
    });

    this.$root.$on('dragEnd', () => {
      this.highlight = false;
    });
  }
}
</script>
