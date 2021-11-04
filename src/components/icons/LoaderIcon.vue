<template>
  <span class="loader-icon_wrapper">
    <svg
      :width="size"
      :height="size"
      viewBox="0 0 18 18"
      fill="none"
      xmlns="http://www.w3.org/2000/svg"
      class="loader-icon"
    >
      <path
        d="M16.0232 3.37196C17.3027 4.96871 18 6.95382 18 9C18 10.864 16.489 12.375 14.625 12.375C12.761 12.375 11.25 10.864 11.25 9C11.2925 9.74341 11.25 8.32585 11.25 9C11.164 7.49465 10.125 5.62501 7.3125 5.62501C3.48911 5.62501 3.58134 10.0925 3.9375 11.25C6.1875 18.5625 13.9555 16.5822 14.7437 15.929C13.1683 17.2348 11.1951 17.9649 9.14914 17.9988C7.10324 18.0327 5.10685 17.3684 3.48911 16.1155C1.87138 14.8626 0.728878 13.0958 0.249977 11.1064C-0.228924 9.11705 -0.0156376 7.02389 0.854673 5.17201C1.72498 3.32014 3.20036 1.82011 5.03756 0.919228C6.87476 0.0183488 8.9641 -0.229595 10.9611 0.216275C12.9581 0.662144 14.7436 1.77521 16.0232 3.37196Z"
        :fill="fill"
      />
      <defs>
        <radialGradient
          id="paint0_angular_4802:187"
          cx="0"
          cy="0"
          r="1"
          gradientUnits="userSpaceOnUse"
          gradientTransform="translate(9 9) rotate(45.0001) scale(10.3414)"
        >
          <stop stop-color="white" />
          <stop offset="1" stop-color="white" stop-opacity="0" />
        </radialGradient>
        <radialGradient
          id="paint0_angular_4802:1871"
          cx="0"
          cy="0"
          r="1"
          gradientUnits="userSpaceOnUse"
          gradientTransform="translate(9 9) rotate(45.0001) scale(10.3414)"
        >
          <stop stop-color="#0066ff" />
          <stop offset="1" stop-color="#0066ff" stop-opacity="0" />
        </radialGradient>
      </defs>
    </svg>
  </span>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

@Component({})
export default class LoaderIcon extends Vue {
  @Prop({
    type: String,
    default: 'paint0_angular_4802:187',
  })
  readonly fill!: 'paint0_angular_4802:187' | 'paint0_angular_4802:1871';

  @Prop({
    type: String,
    default: '18',
  })
  readonly size!: string | number;
}
</script>

<style scoped>
.loader-icon {
  animation: 1.5s linear 0s normal none infinite running rot;
  -webkit-animation: 1.5s linear 0s normal none infinite running rot;
}

@keyframes rot {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@-webkit-keyframes rot {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.loader-icon_wrapper {
  min-width: 18px;
  min-height: 18px;
  align-self: center;
}
</style>
