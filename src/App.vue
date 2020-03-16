<template lang="pug">
  #app(@click="bodyClick")
    b-container
      SelectShape
    b-container
      b-row
        b-col(
          md="8"
        )
          ShapeCuboid(
            v-if="shape === 'cuboid'"
          )
          ShapeCylinder(
            v-if="shape === 'cylinder'"
          )
        b-col(
          md="4"
        )
          Toolbar(v-if="shape")
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import SelectShape from './components/SelectShape.vue';
import ShapeCuboid from './components/Shape/ShapeCuboid.vue';
import ShapeCylinder from './components/Shape/ShapeCylinder.vue';
import Toolbar from './components/Toolbar/Toolbar.vue';

@Component({
  components: {
    SelectShape,
    ShapeCuboid,
    ShapeCylinder,
    Toolbar,
  },
})
export default class App extends Vue {
  shape = '';

  created() {
    this.$root.$on('SelectShape', (e: string) => {
      this.shape = e;
    });
  }

  bodyClick() {
    this.$root.$emit('hidePopups');
  }
}
</script>

<style lang="sass">
#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  color: #2c3e50
  margin-top: 60px
</style>
