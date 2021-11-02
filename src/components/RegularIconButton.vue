<template>
  <BaseButton
    :type="type"
    @mouseenter.native="onHover"
    @mouseleave.native="onHover"
    :onClick="onClick"
    :disabled="disabled"
    :size="size"
    tag="icon"
  >
    {{ text ? text + '&nbsp;' : '' }}

    <slot />
  </BaseButton>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import BaseButton from './ui/BaseButton.vue';

@Component({
  components: {
    BaseButton,
  },
})
export default class RegularButton extends Vue {
  @Prop({
    type: String,
    default: '',
  })
  readonly text!: string;

  @Prop({
    type: String,
    default: 'primary',
  })
  readonly type!: 'primary' | 'black' | 'secondary';

  @Prop({
    type: String,
    default: 'default',
  })
  readonly size!: 'small' | 'default' | 'large';

  @Prop({
    type: Vue,
  })
  readonly icon!: any;

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly disabled!: boolean;

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly isLoading!: boolean;

  @Prop({
    type: Function,
  })
  readonly onClick!: () => Promise<void>;

  hover = false;

  onHover() {
    this.hover = !this.hover;
  }
}
</script>

<style scoped>
.base-icon {
  border-radius: 4px;
  font-weight: 500;
  display: flex;
}

.base-icon-small {
  padding: 2px;
  font-size: 14px;
}
.base-icon-default {
  padding: 4px;
  font-size: 16px;
}
.base-icon-large {
  padding: 6px;
  font-size: 18px;
}

.base-icon:hover > div > .svg-default:first-child {
  opacity: 0;
}

.base-icon.primary {
  color: #fff;
  background: #0066ff;
}

.base-icon.primary:hover {
  background: #0057d9;
}
.base-icon.primary:active {
  transform: scale(0.9);
}
.base-icon.black {
  background: #000;
  color: #fff;
}
.base-icon.black:active {
  transform: scale(0.8);
}

.base-icon.secondary {
  color: #0066ff;
  background: transparent;
  border: 2px #f6f9fc solid;
}

.base-icon.secondary:hover {
  color: #0057d9;
  background: #f6f9fc;
}

.base-icon:disabled,
.base-icon:disabled:hover {
  background: #e8ebf2;
  color: #6e829a;
}
</style>
