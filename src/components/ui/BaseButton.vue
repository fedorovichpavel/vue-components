<template>
  <button @click="click">
    <slot />
  </button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({})
export default class BaseButton extends Vue {
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
button {
  padding: 0;
  margin: 0;
  text-decoration: none;
  color: #000;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;
  transition: 0.4s all;
}
</style>
