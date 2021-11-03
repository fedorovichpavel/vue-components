<template>
  <a @click="click">
    <slot />
  </a>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

type TagName = string;

@Component({})
export default class BaseLink extends Vue {
  @Prop({
    type: Function,
  })
  readonly onClick!: (a: Event) => Promise<void> | any;

  click(event: Event) {
    if (typeof this.onClick === 'function') {
      return this.onClick(event);
    }
    return null;
  }
}
</script>

<style scoped>
a {
  padding: 0;
  margin: 0;
  text-decoration: none;
  color: #000;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;
  transition: 0.4s all;
  display: flex;
}
</style>
