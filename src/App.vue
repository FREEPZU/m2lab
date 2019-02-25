<template>
  <div id="app">
    <Header/>
    <Converter/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Header from './components/Header.vue';
import Converter from './components/Converter.vue';

@Component({
  components: {
    Header,
    Converter,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
  @import '../node_modules/bootstrap/scss/bootstrap.scss';
  body {
    background-color: #37414a;
    color: #FFFFFF;
}

.buy-block {
    background-color: #c2252c;
}

.sell-block {
    background-color: #00b9b3;
}

.border-bottom {
    border-bottom: 1px solid #5c666f !important;
}
</style>
