<template>
  <Shape>
    <Heading :heading="heading" class="heading"/>
    <Subtitle :subtitle="subtitle" class="subtitle"/>
    <Paragraph :text="text" class="paragraph"/>
    <Button :label="label"/>
  </Shape>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Shape from '../base-components/Shape.vue'
import Heading from '../base-components/Heading.vue'
import Subtitle from '../base-components/Subtitle.vue'
import Paragraph from '../base-components/Paragraph.vue'
import Button from '../base-components/Button.vue'


@Component({
  components: {
    Shape,
    Heading,
    Subtitle,
    Paragraph,
    Button
  }
})
export default class CardContent extends Vue {
  @Prop() private heading!: string;
  @Prop() private subtitle!: string;
  @Prop() private text!: string;
  @Prop() private label!: string;
}
</script>

<style scoped>
@import '../../build/css/variables.css';
  .shape{
    text-align: initial;
  }
  .heading{
    margin-bottom: var(--spacing-size-xxxs);
  }
  .subtitle{
    margin-bottom: var(--spacing-size-xxs);
  }
  .paragraph{
    margin-bottom: var(--spacing-size-sm);
  }
</style>
