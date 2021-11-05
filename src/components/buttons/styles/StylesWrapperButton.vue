<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import SameLinkBtnProps from '../props/SameLinkBtnProps.vue';
import ArrowIcon from '../../icons/ArrowIcon.vue';
import LoaderIcon from '../../icons/LoaderIcon.vue';

@Component({
  components: {
    ArrowIcon,
    LoaderIcon,
  },
})
class StylesWrapperButton extends SameLinkBtnProps {
  get loaderFill() {
    return this.type === 'secondary' ||
      (this.tag === 'link' && this.type !== 'black')
      ? 'url(#paint0_angular_4802:1871)'
      : 'url(#paint0_angular_4802:187)';
  }

  get arrowIconClassList() {
    return ['styles-wrapper-button__icon', 'styles-wrapper-button__icon_fill'];
  }
  get classList() {
    return [
      `styles-wrapper-button styles-wrapper-button_size_${this.size}`,
      `styles-wrapper-button_type_${this.type}`,
      `styles-wrapper-button_border-radius-size_${this.border}`,
      this.indent ? `styles-wrapper-button_indent_${this.indent}` : '',
    ];
  }

  render(h: (tagName: any, options: any, children?: any) => HTMLElement) {
    if (
      this.$slots.default &&
      this.$slots.default[0].componentOptions &&
      this.$slots.default[0].componentOptions.children
    ) {
      if (this.isIcon) {
        this.$slots.default[0].componentOptions.children.push(
          this.$createElement(ArrowIcon, {
            attrs: {
              isHover: this.isHover,
            },
            class: this.arrowIconClassList,
          })
        );
      }
      if (this.isLoading) {
        this.$slots.default[0].componentOptions.children.push(
          this.$createElement(LoaderIcon, {
            attrs: {
              isLoading: this.isLoading,
              fill: this.loaderFill,
            },
          })
        );
      }
    }

    return h('div', {}, this.$slots.default);
  }
}
export default StylesWrapperButton;
</script>

<style scoped>
.styles-wrapper-button {
  border-radius: 8px;
  font-weight: 500;
  display: flex;
  align-items: center;
  justify-content: center;
  column-gap: 8px;
  position: relative;
}

.styles-wrapper-button_type_primary {
  color: #fff;
  background: #0066ff;
}

.styles-wrapper-button_type_primary:hover {
  background: #0057d9;
}
.styles-wrapper-button_type_primary:active {
  transform: scale(0.9);
}
.styles-wrapper-button_type_black {
  background: #000;
  color: #fff;
}
.styles-wrapper-button_type_black:active {
  transform: scale(0.8);
}

.styles-wrapper-button_type_secondary {
  color: #6e829a;
  background: transparent;
  border: 2px #f6f9fc solid;
}

.styles-wrapper-button_type_secondary:hover {
  color: #0057d9;
  background: #f6f9fc;
}

.styles-wrapper-button_type_link-primary {
  color: #0066ff;
  background: transparent;
}

.styles-wrapper-button_type_link-primary:hover {
  color: #0057d9;
}

.styles-wrapper-button_type_link-black {
  color: #fff;
  background: transparent;
}

.styles-wrapper-button:disabled,
.styles-wrapper-button:disabled:hover {
  background: #e8ebf2;
  color: #6e829a;
}

.styles-wrapper-button.styles-wrapper-button_size_xxs {
  min-height: 32px;
  min-width: 32px;
}

.styles-wrapper-button.styles-wrapper-button_size_xs {
  min-height: 40px;
  min-width: 40px;
}

.styles-wrapper-button.styles-wrapper-button_size_s {
  min-height: 30px;
  min-width: 90px;
  font-size: 14px;
}

.styles-wrapper-button.styles-wrapper-button_size_m {
  min-height: 36px;
  min-width: 109px;
  font-size: 16px;
}

.styles-wrapper-button.styles-wrapper-button_size_l {
  min-height: 40px;
  min-width: 119px;
  font-size: 18px;
}

.styles-wrapper-button_border-radius-size_s {
  border-radius: 4px;
}

.styles-wrapper-button_border-radius-size_m {
  border-radius: 6px;
}

.styles-wrapper-button_border-radius-size_l {
  border-radius: 8px;
}

.styles-wrapper-button_indent_s {
  padding: 0 5px;
}

.styles-wrapper-button_indent_m {
  padding: 0 10px;
}

.styles-wrapper-button_indent_l {
  padding: 0 20px;
}

/* ICON */

.styles-wrapper-button >>> .styles-wrapper-button__icon {
  position: relative;
  display: flex;
  align-self: center;
  transition: all 0.5s;
  right: 0;
  min-width: 15px;
}

.styles-wrapper-button.styles-wrapper-button_type_primary
  >>> .styles-wrapper-button__icon_fill,
.styles-wrapper-button.styles-wrapper-button_type_black
  >>> .styles-wrapper-button__icon_fill,
.styles-wrapper-button.styles-wrapper-button_type_link-black
  >>> .styles-wrapper-button__icon_fill {
  fill: #fff;
}
.styles-wrapper-button.styles-wrapper-button_type_secondary
  >>> .styles-wrapper-button__icon_fill,
.styles-wrapper-button:disabled >>> .styles-wrapper-button__icon_fill {
  fill: #6e829a;
}

.styles-wrapper-button:hover.styles-wrapper-button_type_secondary
  >>> .styles-wrapper-button__icon_fill,
.styles-wrapper-button.styles-wrapper-button_type_link-primary
  >>> .styles-wrapper-button__icon_fill {
  fill: #0057d9;
}

.styles-wrapper-button >>> .styles-wrapper-button__icon::after {
  position: absolute;
  content: '';
  height: 2px;
  width: 0;
  top: 50%;
  left: 4px;
  transform: translate(50%, -50%);
  transition: all 0.3s;
}

.styles-wrapper-button.styles-wrapper-button_type_primary
  >>> .styles-wrapper-button__icon_fill::after,
.styles-wrapper-button.styles-wrapper-button_type_black
  >>> .styles-wrapper-button__icon_fill::after,
.styles-wrapper-button.styles-wrapper-button_type_link-black
  >>> .styles-wrapper-button__icon_fill::after {
  background: #fff;
}

.styles-wrapper-button:hover.styles-wrapper-button_type_secondary
  >>> .styles-wrapper-button__icon_fill::after,
.styles-wrapper-button.styles-wrapper-button_type_link-primary
  >>> .styles-wrapper-button__icon_fill::after {
  background: #0057d9;
}

.styles-wrapper-button:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon,
.styles-wrapper-button-link:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon {
  right: -9px;
}

.styles-wrapper-button:disabled:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon,
.styles-wrapper-button-link:disabled:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon {
  right: 0;
}

.styles-wrapper-button:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon::after,
.styles-wrapper-button-link:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon::after {
  width: 9px;
  left: -9px;
}

.styles-wrapper-button:disabled:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon::after,
.styles-wrapper-button-link:disabled:hover.styles-wrapper-button
  >>> .styles-wrapper-button__icon::after {
  width: 0;
}
</style>
