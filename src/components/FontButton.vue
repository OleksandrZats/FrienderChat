<template>
  <button
    class="fontButton"
    @click="changeFnt(this.font)"
    v-bind:class="{ activeFont: this.chatFont == this.font }"
  >
    {{ font }}
  </button></template
>
<script>
export default {
  props: ["font", "chatFont"],
  methods: {
    changeFnt(fnt) {
      this.$emit("changeFnt", {
        font: fnt,
      });

      console.log("font");
    },
  },
};
</script>
<style>
.fontButton {
  min-width: 300px;
  min-height: 40px;
  margin-bottom: 24px;
  background: transparent;
  border: none;
  cursor: pointer;
  text-align: center;
  text-justify: center;
  border: 2px solid #fff;
  border-radius: 8px;
}
.activeFont {
  border-color: #3b5a9c;
}
</style>
