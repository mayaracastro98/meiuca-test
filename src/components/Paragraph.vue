<template>
  <p :style="computedStyle">{{text}}</p>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Meiuca } from '../../build/css/colors'


@Component
export default class Paragraph extends Vue {
  @Prop() private text!: string;

  @Prop({ type: String, default: Meiuca.neutralColor4 })
  private color!: Meiuca

  @Prop({ type: String, default: Meiuca.fontFamilyHighlighht })
  private fontFamily!: Meiuca

  @Prop({ type: String, default: Meiuca.fontWeightRegular })
  private fontWeight!: Meiuca

    private get computedStyle() {
    return `color: ${this.color}; font-family: ${this.fontFamily}; font-weight: ${this.fontWeight};`
    }
}
</script>

<style scoped>
@import '../../build/css/variables.css';
p {
    font-size: var(--font-size-xs);
    line-height: var(--line-height-distant);
}
</style>
