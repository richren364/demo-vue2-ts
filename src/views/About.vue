<template>
  <div class="about">
    <h1>This is an about page</h1>
    <DemoElement></DemoElement>
  </div>
</template>
<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import DemoElement from "@/components/DemoElement.vue";

@Component({
  components: {
    DemoElement,
  },
})
export default class About extends Vue {}
</script>
