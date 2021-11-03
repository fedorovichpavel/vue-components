<template>
  <component
    :is="tagName"
    @mouseenter.native="onHover"
    @mouseleave.native="onHover"
    :onClick="onClick"
    :disabled="isDisabled"
    :class="className"
  >
    <slot />
    <LoaderIcon v-if="isLoading" :fill="loaderFill" />
    <ArrowIcon
      v-else-if="isIcon"
      :isHover="isHover"
      :fill="arrowIconFill"
      :class="arrowIconClassName"
    />
  </component>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import BaseButton from './ui/BaseButton.vue';
import BaseLink from './ui/BaseLink.vue';
import ArrowIcon from './icons/ArrowIcon.vue';
import LoaderIcon from './icons/LoaderIcon.vue';

@Component({
  components: {
    BaseLink,
    BaseButton,
    ArrowIcon,
    LoaderIcon,
  },
})
export default class RegularButton extends Vue {
  @Prop({
    type: String,
  })
  readonly text!: string;

  @Prop({
    type: String,
    default: 'button',
  })
  readonly tag!: 'link' | 'button' | 'icon';

  @Prop({
    type: String,
    default: 'primary',
  })
  readonly type!: 'primary' | 'black' | 'secondary';

  @Prop({
    type: String,
    default: 's',
  })
  readonly size!: 's' | 'm' | 'l';

  @Prop({
    type: String,
    default: 'm',
  })
  readonly border!: 's' | 'm' | 'l';

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly isIcon!: boolean;

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
  readonly onClick!: () => Promise<void> | any;

  isHover = false;

  onHover() {
    this.isHover = !this.isHover;
  }

  get className() {
    switch (this.tag) {
      case 'link':
        return `base-link base-link_size_${this.size} base-link_type_${this.type} base-link_border-radius-size_${this.border}`;
      case 'icon':
        return `base-button base-button-icon_size_${this.size} base-button_type_${this.type} base-button_border-radius-size_${this.border}`;
      default:
        return `base-button base-button_size_${this.size} base-button_type_${this.type} base-button_border-radius-size_${this.border}`;
    }
  }

  get loaderFill() {
    return this.type === 'secondary' ||
      (this.tag === 'link' && this.type !== 'black')
      ? 'url(#paint0_angular_4802:1871)'
      : 'url(#paint0_angular_4802:187)';
  }

  get arrowIconFill() {
    return this.isDisabled ||
      (this.tag === 'button' && this.type === 'secondary' && !this.isHover)
      ? '#6E829A'
      : this.type === 'secondary' ||
        (this.tag === 'link' && this.type !== 'black')
      ? '#0066FF'
      : 'white';
  }

  get arrowIconClassName() {
    return `base-button__icon base-button__icon_color_${
      this.type === 'secondary' ||
      (this.tag === 'link' && this.type === 'primary')
        ? 'blue'
        : 'white'
    }`;
  }

  get tagName() {
    return this.tag === 'link' ? 'BaseLink' : 'BaseButton';
  }
}
</script>

<style scoped>
.base-button {
  border-radius: 8px;
  font-weight: 500;
  display: flex;
  align-items: center;
  justify-content: center;
  column-gap: 8px;
  position: relative;
}

.base-button__icon {
  position: relative;
  display: flex;
  align-self: center;
  transition: all 0.5s;
  right: 0;
}

.base-button__icon::after {
  position: absolute;
  content: '';
  height: 2px;
  width: 0;
  top: 45%;
  left: 4px;
  transform: translateX(50%);
  transition: all 0.5s;
}

.base-button__icon_color_white::after {
  background: #fff;
}
.base-button__icon_color_blue::after {
  background: #0057d9;
}

.base-button:hover .base-button__icon,
.base-link:hover .base-button__icon {
  right: -9px;
}

.base-button:disabled:hover .base-button__icon,
.base-link:disabled:hover .base-button__icon {
  right: 0;
}

.base-button:hover .base-button__icon::after,
.base-link:hover .base-button__icon::after {
  width: 12px;
  left: -12px;
}

.base-button:disabled:hover .base-button__icon::after,
.base-link:disabled:hover .base-button__icon::after {
  width: 0;
}

.base-button_size_s {
  min-height: 30px;
  min-width: 90px;
  font-size: 14px;
}
.base-button_size_m {
  min-height: 36px;
  min-width: 109px;
  font-size: 16px;
}
.base-button_size_l {
  min-height: 40px;
  min-width: 119px;
  font-size: 18px;
}

.base-button-icon_size_s {
  min-height: 32px;
  min-width: 32px;
}
.base-button-icon_size_m {
  min-height: 36px;
  min-width: 36px;
}
.base-button-icon_size_l {
  min-height: 40px;
  min-width: 40px;
}

.base-button_type_primary {
  color: #fff;
  background: #0066ff;
}

.base-button_type_primary:hover {
  background: #0057d9;
}
.base-button_type_primary:active {
  transform: scale(0.9);
}
.base-button_type_black {
  background: #000;
  color: #fff;
}
.base-button_type_black:active {
  transform: scale(0.8);
}

.base-button_type_secondary {
  color: #6e829a;
  background: transparent;
  border: 2px #f6f9fc solid;
}

.base-button_type_secondary:hover {
  color: #0057d9;
  background: #f6f9fc;
}

.base-button_border-radius-size_s {
  border-radius: 4px;
}

.base-button_border-radius-size_m {
  border-radius: 6px;
}

.base-button_border-radius-size_l {
  border-radius: 8px;
}

.base-link {
  min-width: 70px;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  padding: relative;
}

.base-link_type_primary {
  color: #0066ff;
}

.base-link_type_primary:hover {
  color: #0057d9;
}

.base-link_type_black {
  color: #fff;
}

.base-button:disabled,
.base-button:disabled:hover {
  background: #e8ebf2;
  color: #6e829a;
}
</style>
