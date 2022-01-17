<template>
  <h1 :style="computedStyle">{{heading}}</h1>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Meiuca } from '../../build/css/colors'

@Component
export default class Heading extends Vue {
  @Prop() private heading!: string;

  @Prop({ type: String, default: Meiuca.neutralColor5 })
  private color!: Meiuca

  @Prop({ type: String, default: Meiuca.fontFamilyHighlighht })
  private fontFamily!: Meiuca

  @Prop({ type: String, default: Meiuca.fontWeightBold })
  private fontWeight!: Meiuca

    private get computedStyle() {
    return `color: ${this.color}; font-family: ${this.fontFamily}; font-weight: ${this.fontWeight};`
    }
}
</script>

<style scoped>
@import '../../build/css/variables.css';
h1 {
    font-size: var(--font-size-lg);
    line-height: var(--line-height-distant);
}
</style>
