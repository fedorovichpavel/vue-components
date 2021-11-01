<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

type TagName = string;

@Component({
  methods: {
    click() {
      console.log(this);
    },
  },
})
export default class BaseButton extends Vue {
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

  render(h: (tagName: TagName, options: any, children?: any) => HTMLElement) {
    return this.tag === 'link'
      ? h('a', {}, this.text)
      : h(
          'button',
          {
            attrs: {
              class: `base-button ${this.type}`,
              disabled: false,
            },
          },
          this.text
        );
  }
}
</script>

<style scoped>
button,
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
}

.base-button {
  padding: 6px 12px;
  border-radius: 8px;
  font-weight: 500;
  font-size: 16px;
}

.primary {
  color: #fff;
  background: #0066ff;
}

.primary:hover {
  background: #0057d9;
}
.primary:active {
  transform: scale(0.9);
}

button:disabled,
button:disabled:hover {
  background: #e8ebf2;
  color: #6e829a;
}

.black {
  background: #000;
  color: #fff;
}
.black:active {
  transform: scale(0.8);
}
</style>
