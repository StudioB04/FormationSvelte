<script>
  import { marked } from "marked"; 

  export default {
    name: "Alert",
    props: {
      icon: { type: String, required: false },
      color: { type: String, required: false },
      title: { type: String, required: false },
      text: { type: String, required: true },
    },
    computed: {
      renderedText() {
        return marked(this.text || "");
      },
    },
  };
</script>

<template>
  <blockquote flex flex-col>
    <div :class="`text-${color}`">
      <carbon-information v-if="icon"/> 
      {{title}}
    </div>
    <div v-html="renderedText"></div>
  </blockquote>
</template>