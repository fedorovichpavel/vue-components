<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

type TagName = string;

@Component({})
export default class BaseLink extends Vue {
  @Prop({
    type: String,
    default: 'primary',
  })
  readonly type!: 'primary' | 'black' | 'secondary';

  @Prop({
    type: String,
    default: 'default',
  })
  readonly size!: 'small' | 'default' | 'large';

  @Prop({
    type: Function,
  })
  readonly onClick!: (a: Event) => Promise<void>;

  click(event: Event) {
    if (typeof this.onClick === 'function') {
      return this.onClick(event);
    }
    return null;
  }

  render(h: (tagName: TagName, options: any, children?: any) => HTMLElement) {
    return h(
      'a',
      {
        attrs: {
          class: `base-link base-link-${this.size} ${this.type}`,
        },
        on: {
          click: this.click,
        },
      },
      this.$slots.default
    );
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
