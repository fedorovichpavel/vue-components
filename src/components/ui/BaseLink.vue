<template>
  <a @click="click" :href="href" :target="target" class="base-link">
    <slot />
  </a>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({})
export default class BaseLink extends Vue {
  @Prop({
    type: String,
  })
  readonly href!: string;

  @Prop({
    type: String,
    default: '_self',
  })
  readonly target!: '_self' | '_blank' | '_parent' | '_top';

  @Prop({
    type: Function,
  })
  readonly onClick!: <T>(a: Event) => Promise<T> | T;

  click(event: Event) {
    if (typeof this.onClick === 'function') {
      return this.onClick(event);
    }
    return null;
  }
}
</script>

<style scoped>
.base-link {
  padding: 0;
  margin: 0;
  text-decoration: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;
  transition: 0.4s all;
  display: flex;
}
</style>
