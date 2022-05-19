<template>
  <div class="app">
    <h1>{{ title }}</h1>
    <Imagedata />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Imagedata from "./components/imageView.vue";

@Options({
  components: {
    Imagedata,
  },
})
export default class App extends Vue {
  public title = "Image List";
}
</script>

<style>
.app h1 {
  text-align: center;
  color: #7c795d;
  font-family: "Trocchi", serif;
  font-size: 45px;
  font-weight: normal;
  line-height: 48px;
  margin: 0;
  margin-top: 20px;
}
</style>
