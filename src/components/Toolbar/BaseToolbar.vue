<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class ToolbarProperty extends Vue {
  value = '';

  proptype = '';

  name = '';

  get propsData() {
    return JSON.stringify({
      // type: this.proptype,
      name: this.name,
      value: this.value,
    });
  }

  dragStart(e: DragEvent) {
    if (e.dataTransfer) {
      this.$root.$emit('dragStart', this.name);
      e.dataTransfer.setData('text/plain', this.propsData);
    }
  }

  dragEnd() {
    this.$root.$emit('dragEnd');
  }
}
</script>

<style scoped lang="sass"></style>
