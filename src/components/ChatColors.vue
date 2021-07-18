<template>
  <div class="miniatures">
    <h3>Choose template</h3>
    <div class="mini" v-for="color in this.colors" :key="color">
      <ChatMini
        :color="color"
        :chatColor="this.chatColor"
        @changeClr="changeClr"
      />
    </div>
  </div>
</template>

<script>
import ChatMini from "@/components/ChatMini";
export default {
  props: ["colors", "chatColor"],
  components: { ChatMini },
  methods: {
    changeClr(clr) {
      this.$emit("changeClr", {
        color: clr.color,
      });
    },
  },
};
</script>
<style>
h3 {
  font-family: Inter;
  font-weight: 600;
  font-size: 16px;
  line-height: 24px;
  width: 100%;
}
.miniatures {
  display: flex;
  flex-wrap: wrap;
  padding: 24px 0px 24px 24px;
  align-items: center;
  justify-content: center;
}
.mini {
  margin: 24px 24px 0px 0px;
}
</style>
