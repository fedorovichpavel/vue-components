<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
@Component
export default class SameLinkBtnProps extends Vue {
  @Prop({
    type: String,
    default: 'button',
  })
  readonly tag!: 'link' | 'button' | 'icon';

  @Prop({
    type: String,
    default: 'primary',
  })
  readonly type!:
    | 'primary'
    | 'black'
    | 'secondary'
    | 'link-primary'
    | 'link-black';

  @Prop({
    type: String,
    default: 's',
  })
  readonly size!: 'xxs' | 'xs' | 's' | 'm' | 'l';

  @Prop({
    type: String,
    default: 'm',
  })
  readonly border!: 's' | 'm' | 'l';

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly isIcon!: boolean;

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly isDisabled!: boolean;

  @Prop({
    type: Boolean,
    default: false,
  })
  readonly isLoading!: boolean;

  isHover = false;

  onHover() {
    this.isHover = !this.isHover;
  }
}
</script>
