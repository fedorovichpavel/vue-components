<template>
  <transition-group name="fade">
    <svg
      class="svg-default"
      width="8"
      height="12"
      viewBox="0 0 8 12"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      v-if="!hover"
      key="svg-1"
    >
      <path
        d="M0.0131226 10.59L4.59312 6L0.0131226 1.41L1.42312 0L7.42312 6L1.42312 12L0.0131226 10.59Z"
        :fill="
          disabled
            ? '#6E829A'
            : type === 'secondary' || (tag === 'link' && type !== 'black')
            ? '#0066FF'
            : 'white'
        "
      />
    </svg>
    <svg
      width="13"
      height="12"
      viewBox="0 0 13 12"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      class="svg-hovered"
      key="svg-2"
      v-else
    >
      <path
        fill-rule="evenodd"
        clip-rule="evenodd"
        d="M5.71694 9.88462C5.32809 10.2743 5.32843 10.9053 5.71771 11.2946C6.10728 11.6842 6.7389 11.6842 7.12848 11.2946L11.4231 7L12.4231 6L11.4231 5L7.12848 0.705388C6.7389 0.315815 6.10728 0.315815 5.71771 0.705388C5.32843 1.09466 5.32809 1.72569 5.71694 2.11539L8.59527 5H1.4231C0.870811 5 0.423096 5.44772 0.423096 6C0.423096 6.55228 0.870811 7 1.4231 7H8.59527L5.71694 9.88462Z"
        :fill="
          disabled
            ? '#6E829A'
            : type === 'secondary' || (tag === 'link' && type !== 'black')
            ? '#0066FF'
            : 'white'
        "
      />
    </svg>
  </transition-group>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

@Component({})
export default class ArrowIcon extends Vue {
  @Prop({
    type: Boolean,
  })
  readonly hover!: boolean;

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly disabled!: boolean;

  @Prop({
    type: String,
    default: 'primary',
  })
  readonly type!: 'primary' | 'black' | 'secondary';

  @Prop({
    type: String,
    default: 'button',
  })
  readonly tag!: 'link' | 'button';
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.fade-leave-to.svg-default {
  right: -7px;
}
.fade-leave-to.svg-hovered {
  right: 0;
}

svg {
  position: absolute;
  transition: 0.3s all;
}
span {
  padding-left: 8px;
  width: 13px;
  height: 12px;
  align-self: center;
  position: relative;
}
</style>
