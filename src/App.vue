<template>
  <div id="app">
    <RegularButton
      type="primary"
      text="Primary"
      tag="button"
      @click.native="click"
    />
    <RegularButton type="black" text="Black" tag="button" />

    <button @click="click"><a>Add</a></button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import RegularButton from './components/RegularButton.vue';

@Component({
  components: {
    RegularButton,
  },
  methods: {
    click() {
      console.log(this);
    },
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  column-gap: 30px;
  justify-content: center;
}
</style>
