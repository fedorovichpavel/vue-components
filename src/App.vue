<template>
  <div id="app" class="app">
    <h1 class="app__title">Promo site Buttons</h1>
    <h2>Buttons</h2>
    <div class="app__promo-btns">
      <RegularButton
        type="primary"
        tag="button"
        isIcon
        :onClick="click"
        :isLoading="isLoading"
        >Action</RegularButton
      >
      <RegularButton type="black" tag="button" isIcon>Black</RegularButton>
      <RegularButton type="secondary" tag="button" isIcon
        >Secondary</RegularButton
      >
    </div>
    <div class="app__promo-btns">
      <RegularButton type="primary" tag="button" size="s"
        >Primary</RegularButton
      >
      <RegularButton
        type="black"
        tag="button"
        :onClick="click2"
        :isLoading="isLoading2"
        >Black</RegularButton
      >
      <RegularButton type="secondary" tag="button">Secondary</RegularButton>
    </div>
    <div class="app__promo-btns">
      <RegularButton type="primary" tag="button" size="s"
        >Primary</RegularButton
      >
      <RegularButton
        type="primary"
        tag="button"
        size="l"
        :onClick="click3"
        :isLoading="isLoading3"
        >Primary</RegularButton
      >
      <RegularButton type="primary" tag="button">Primary</RegularButton>
    </div>
    <div class="app__promo-btns">
      <RegularButton type="black" tag="button" size="s">Black</RegularButton>
      <RegularButton type="black" tag="button" size="l">Black</RegularButton>
      <RegularButton type="black" tag="button">Black</RegularButton>
    </div>
    <div class="app__promo-btns">
      <RegularButton type="primary" tag="button" isDisabled
        >Primary</RegularButton
      >
      <RegularButton type="black" tag="button" isIcon isDisabled
        >Black</RegularButton
      >
      <RegularButton type="secondary" tag="button" isDisabled
        >Secondary</RegularButton
      >
    </div>
    <div class="app__promo-btns">
      <RegularButton type="primary" tag="button" isLoading
        >Primary</RegularButton
      >
      <RegularButton type="black" tag="button" isLoading>Black</RegularButton>
      <RegularButton type="secondary" tag="button" isLoading
        >Secondary</RegularButton
      >
    </div>
    <div class="app__promo-btns">
      <RegularButton type="primary" tag="button">Primary</RegularButton>
      <RegularButton type="black" tag="button">Black</RegularButton>
      <RegularButton type="secondary" tag="button">Secondary</RegularButton>
    </div>
    <h2>Icons</h2>
    <div class="app__promo-btns">
      <RegularIconButton type="primary" size="xxs"
        ><TestIcon
      /></RegularIconButton>
      <RegularIconButton type="black" size="xxs"
        ><TestIcon
      /></RegularIconButton>
      <RegularIconButton type="secondary" size="xxs"
        ><TestIcon
      /></RegularIconButton>
    </div>
    <div class="app__promo-btns">
      <RegularButton type="primary" tag="button" size="s" border="s">
        Primary <TestIcon />
      </RegularButton>
      <RegularButton type="black" tag="button" size="s" border="s">
        Black <TestIcon />
      </RegularButton>
      <RegularButton type="secondary" tag="button" size="s" border="s">
        Secondary <TestIcon />
      </RegularButton>
    </div>
    <h2>Links</h2>
    <div class="app__promo-btns">
      <RegularLink type="link-black" tag="link" isIcon>Black</RegularLink>
      <RegularLink type="link-black" tag="link">Black</RegularLink>
      <RegularLink type="link-primary" tag="link" isIcon>Black</RegularLink>
      <RegularLink type="link-primary" tag="link">Black</RegularLink>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import RegularButton from './components/RegularButton.vue';
import RegularLink from './components/RegularLink.vue';
import RegularIconButton from './components/RegularIconButton.vue';
import TestIcon from './components/icons/TestIcon.vue';

@Component({
  components: {
    RegularButton,
    RegularLink,
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
.app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px 120px;
}
.app__title {
  font-weight: 500;
  font-size: 60px;
  line-height: 70px;
  color: #000;
  text-align: left;
}

.app__promo-btns {
  display: flex;
  align-items: center;
  column-gap: 30px;
  justify-content: center;
  padding-bottom: 60px;
}

.app__promo-btns:last-child {
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
