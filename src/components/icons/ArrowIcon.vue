<template>
  <span
    ><svg
      class="arrow-icon"
      width="8"
      height="12"
      viewBox="0 0 8 12"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        d="M0.0131226 10.59L4.59312 6L0.0131226 1.41L1.42312 0L7.42312 6L1.42312 12L0.0131226 10.59Z"
      /></svg
  ></span>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

@Component({})
export default class ArrowIcon extends Vue {}
</script>

<style scoped>
.arrow-icon {
  fill: inherit;
}
</style>
