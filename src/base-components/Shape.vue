<template>
  <div class="shape" :style="computedStyle">
     <slot />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Meiuca } from '../../build/css/colors'


@Component
export default class Shape extends Vue {
  @Prop({ type: String, default: Meiuca.neutralColor1 })
  private backgroundColor!: Meiuca

    private get computedStyle() {
    return `background-color: ${this.backgroundColor};`
    }

}
</script>

<style scoped>
@import '../../build/css/variables.css';
.shape {
    width: 300px;
    height: 427px;
    border-radius: var(--radius-size-none);
    padding: 40px;
    border-width: var(--border-size-thin);
    border-color: var(--neutral-color-2);
}
</style>
