<template>
  <div class="fontCustomize">
    <h3>Choose font</h3>
    <div class="button" v-for="font in this.fonts">
      <FontButton
        :font="font"
        :chatFont="this.chatFont"
        @changeFnt="changeFnt"
      />
    </div>
  </div>
</template>
<script>
import FontButton from "@/components/FontButton";
export default {
  props: ["fonts", "chatFont"],
  methods: {
    changeFnt(fnt) {
      this.$emit("changeFnt", {
        font: fnt.font,
      });
    },
  },
  components: {
    FontButton,
  },
};
</script>
<style>
.fontCustomize {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 24px;
  width: 100%;
}
</style>
