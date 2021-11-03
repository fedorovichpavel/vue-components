<template>
  <RegularButton
    :type="type"
    @mouseenter.native="onHover"
    @mouseleave.native="onHover"
    :onClick="onClick"
    :isDisabled="isDisabled"
    :size="size"
    :border="border"
    tag="icon"
  >
    <slot />
  </RegularButton>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import RegularButton from './RegularButton.vue';

@Component({
  components: {
    RegularButton,
  },
})
export default class RegularButtonIcon extends Vue {
  @Prop({
    type: String,
    default: 'primary',
    validator: (val) => {
      return ['primary', 'black', 'secondary'].includes(val);
    },
  })
  readonly type!: 'primary' | 'black' | 'secondary';

  @Prop({
    type: String,
    default: 's',
  })
  readonly size!: 's' | 'm' | 'l';

  @Prop({
    type: String,
    default: 's',
  })
  readonly border!: 's' | 'm' | 'l';

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly isDisabled!: boolean;

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly isLoading!: boolean;

  @Prop({
    type: Function,
  })
  readonly onClick!: <Type>() => Type | Promise<Type>;

  hover = false;

  onHover() {
    this.hover = !this.hover;
  }
}
</script>

<style scoped></style>
