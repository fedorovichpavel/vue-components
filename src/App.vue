<template>
  <div id="app">
    <h1>Promo site Buttons</h1>
    <h2>Buttons</h2>
    <div class="promo-btns">
      <RegularButton
        type="primary"
        text="Primary"
        tag="button"
        icon
        :onClick="click"
        :isLoading="isLoading"
      />
      <RegularButton type="black" text="Black" tag="button" icon />
      <RegularButton type="secondary" text="Secondary" tag="button" icon />
    </div>
    <div class="promo-btns">
      <RegularButton type="primary" text="Primary" tag="button" size="small" />
      <RegularButton
        type="black"
        text="Black"
        tag="button"
        :onClick="click2"
        :isLoading="isLoading2"
      />
      <RegularButton type="secondary" text="Secondary" tag="button" />
    </div>
    <div class="promo-btns">
      <RegularButton type="primary" text="Primary" tag="button" size="small" />
      <RegularButton
        type="primary"
        text="Primary"
        tag="button"
        size="large"
        :onClick="click3"
        :isLoading="isLoading3"
      />
      <RegularButton type="primary" text="Primary" tag="button" />
    </div>
    <div class="promo-btns">
      <RegularButton type="black" text="Primary" tag="button" size="small" />
      <RegularButton type="black" text="Primary" tag="button" size="large" />
      <RegularButton type="black" text="Primary" tag="button" />
    </div>
    <div class="promo-btns">
      <RegularButton type="primary" text="Primary" tag="button" disabled />
      <RegularButton type="black" text="Black" tag="button" icon disabled />
      <RegularButton type="secondary" text="Secondary" tag="button" disabled />
    </div>
    <div class="promo-btns">
      <RegularButton type="primary" text="Primary" tag="button" isLoading />
      <RegularButton type="black" text="Black" tag="button" isLoading />
      <RegularButton type="secondary" text="Secondary" tag="button" isLoading />
    </div>
    <div class="promo-btns">
      <RegularButton type="primary" text="Primary" tag="button" />
      <RegularButton type="black" text="Black" tag="button" />
      <RegularButton type="secondary" text="Secondary" tag="button" />
    </div>
    <h2>Icons</h2>
    <div class="promo-btns">
      <RegularIconButton type="primary"><TestIcon /></RegularIconButton>
      <RegularIconButton type="black"><TestIcon /></RegularIconButton>
      <RegularIconButton type="secondary"><TestIcon /></RegularIconButton>
    </div>
    <div class="promo-btns">
      <RegularIconButton text="primary" type="primary"
        ><TestIcon
      /></RegularIconButton>
      <RegularIconButton text="black" type="black"
        ><TestIcon
      /></RegularIconButton>
      <RegularIconButton text="secondary" type="secondary"
        ><TestIcon
      /></RegularIconButton>
    </div>
    <h2>Links</h2>
    <div class="promo-btns">
      <RegularButton type="black" text="Black" tag="link" icon />
      <RegularButton type="black" text="Black" tag="link" />
      <RegularButton type="primary" text="Black" tag="link" icon />
      <RegularButton type="primary" text="Black" tag="link" />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import RegularButton from './components/RegularButton.vue';
import RegularIconButton from './components/RegularIconButton.vue';
import TestIcon from './components/icons/TestIcon.vue';

@Component({
  components: {
    RegularButton,
    RegularIconButton,
    TestIcon,
  },
})
export default class App extends Vue {
  isLoading = false;
  isLoading2 = false;
  isLoading3 = false;

  click(event: Event) {
    this.isLoading = true;
    setTimeout(() => {
      this.isLoading = false;
    }, 3000);
    console.log(event);
  }

  click2(event: Event) {
    this.isLoading2 = true;
    setTimeout(() => {
      this.isLoading2 = false;
    }, 3000);
    console.log(event);
  }

  click3(event: Event) {
    this.isLoading3 = true;
    setTimeout(() => {
      this.isLoading3 = false;
    }, 3000);
    console.log(event);
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px 120px;
}
h1 {
  font-weight: 500;
  font-size: 60px;
  line-height: 70px;
  color: #000;
  text-align: left;
}

.promo-btns {
  display: flex;
  align-items: center;
  column-gap: 30px;
  justify-content: center;
  padding-bottom: 60px;
}

.promo-btns:last-child {
  background: linear-gradient(
    to right,
    transparent 0%,
    transparent 30%,
    #000 30%,
    #000 50%,
    #fff 50%,
    #fff 80%
  );
}
</style>
