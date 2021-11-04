<template>
  <StylesWrapperButton
    :isLoading="isLoading"
    :isIcon="isIcon"
    :type="type"
    :tag="tag"
    :disabled="isDisabled"
    :isHover="isHover"
  >
    <BaseButton
      @mouseenter.native="onHover"
      @mouseleave.native="onHover"
      :onClick="onClick"
      :disabled="isDisabled"
      :class="className"
    >
      <slot />
    </BaseButton>
  </StylesWrapperButton>
</template>

<script lang="ts">
import { Component, Mixins } from 'vue-property-decorator';
import BaseButton from './ui/BaseButton.vue';
import ArrowIcon from './icons/ArrowIcon.vue';
import LoaderIcon from './icons/LoaderIcon.vue';
import StylesWrapperButton from './ui/StylesWrapperButton.vue';

@Component({
  components: {
    StylesWrapperButton,
    BaseButton,
    ArrowIcon,
    LoaderIcon,
  },
})
export default class RegularButton extends Mixins(
  StylesWrapperButton,
  BaseButton
) {}
</script>

<style scoped></style>
