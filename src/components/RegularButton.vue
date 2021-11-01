<template>
  <BaseButton :type="type" :tag="tag" :text="text" />
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import BaseButton from './BaseButton.vue';

@Component({
  components: {
    BaseButton,
  },
})
export default class RegularButton extends Vue {
  @Prop({
    type: String,
    required: true,
  })
  readonly text!: string;
  @Prop({
    type: String,
    default: 'button',
  })
  readonly tag!: 'link' | 'button';
  @Prop({
    type: String,
    default: 'primary',
  })
  readonly type!: 'primary' | 'black';
}
</script>

<style scoped></style>
