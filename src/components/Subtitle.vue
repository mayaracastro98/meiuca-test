<template>
  <h2 :style="computedStyle">{{subtitle}}</h2>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Meiuca } from '../../build/css/colors'


@Component
export default class Subtitle extends Vue {
  @Prop() private subtitle!: string;

  @Prop({ type: String, default: Meiuca.neutralColor4 })
  private color!: Meiuca

  @Prop({ type: String, default: Meiuca.fontFamilyHighlighht })
  private fontFamily!: Meiuca

  @Prop({ type: String, default: Meiuca.fontWeightMedium })
  private fontWeight!: Meiuca

    private get computedStyle() {
    return `color: ${this.color}; font-family: ${this.fontFamily}; font-weight: ${this.fontWeight};`
    }
}
</script>

<style scoped>
@import '../../build/css/variables.css';
h2 {
    font-size: var(--font-size-md);
    line-height: var(--line-height-medium);
}
</style>
