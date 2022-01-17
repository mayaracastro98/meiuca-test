<template>
  <button type="button" 
    :style="computedStyle"
    @mouseover="setHover(true)"
    @mouseleave="setHover(false)"
  >
    {{label}}
  </button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { Meiuca } from '../../build/css/colors'

@Component
export default class Button extends Vue {
  @Prop() private label!: string;

  @Prop({ type: String, default: Meiuca.brandColorPrimary3 })
  private backgroundColor!: Meiuca

   @Prop({ type: String, default: Meiuca.brandColorPrimary4 })
  private hoverColor!: Meiuca

  @Prop({ type: String, default: Meiuca.neutralColor1 })
  private color!: Meiuca

  @Prop({ type: String, default: Meiuca.fontFamilyHighlighht })
  private fontFamily!: Meiuca

  @Prop({ type: String, default: Meiuca.fontWeightMedium })
  private fontWeight!: Meiuca

  private hover = false

    private get computedBGColor(): string {
    let bgColor = this.backgroundColor || Meiuca.brandColorPrimary3

    if (this.hover === true) {
      bgColor = this.hoverColor || Meiuca.brandColorPrimary4
    }

    return bgColor
  }


  private get computedStyle() {
    return `background-color:${this.computedBGColor}; color: ${this.color}; font-family: ${this.fontFamily}; font-weight: ${this.fontWeight};`
    }

    private setHover(value: boolean): void {
      this.hover = value
  }
  }
</script>

<style scoped>
@import '../../build/css/variables.css';
    button {
    cursor: pointer;
    font-size: var(--font-size-sm);
    line-height: var(--line-height-tight);
    border: none;
    border-radius:  var(--radius-size-none);
    padding: var(--spacing-squish-size-xs-v) var(--spacing-squish-size-sm-h);
}

</style>
