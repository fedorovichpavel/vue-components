<template>
  <StylesWrapperButton
    :isLoading="isLoading"
    :isIcon="isIcon"
    :type="type"
    :tag="tag"
    :disabled="isDisabled"
    :isHover="isHover"
  >
    <BaseLink
      @mouseenter.native="onHover"
      @mouseleave.native="onHover"
      :onClick="onClick"
      :disabled="isDisabled"
      :class="classList"
      :href="href"
      :target="target"
    >
      <slot />
    </BaseLink>
  </StylesWrapperButton>
</template>

<script lang="ts">
import { Component, Mixins } from 'vue-property-decorator';
import BaseLink from '../ui/BaseLink.vue';
import ArrowIcon from '../icons/ArrowIcon.vue';
import LoaderIcon from '../icons/LoaderIcon.vue';

import StylesWrapperButton from './styles/StylesWrapperButton.vue';

@Component({
  components: {
    StylesWrapperButton,
    BaseLink,
    ArrowIcon,
    LoaderIcon,
  },
})
export default class RegularButton extends Mixins(
  StylesWrapperButton,
  BaseLink
) {}
</script>

<style scoped></style>
