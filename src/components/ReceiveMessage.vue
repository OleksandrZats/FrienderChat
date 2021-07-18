<template>
  <div
    class="receiveMessage"
    :style="'--receiveMessageColor: ' + receiveMessageColor"
  >
    <p class="receiveMessage__text">{{ messageText }}</p>
    <p class="receiveMessage__time">{{ datetime }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      receiveMessageColor: "#EBEBEB",
      messageText: "Lorem ipsum dolor sit amet consectetur.",
      datetime: "6:06 PM",
    };
  },
  components: {},
};
</script>

<style scoped>
.receiveMessage {
  background-color: var(--receiveMessageColor);
  border-radius: 8px;
  padding: 8px 16px;
  margin: 0 41px 16px 16px;
}
.receiveMessage__text {
  font-size: calc(16px + var(--deltaFontSize));
  line-height: 24px;

  display: flex;
  align-items: center;

  color: #000000;
}

.receiveMessage__time {
  font-size: calc(12px + var(--deltaFontSize));
  line-height: 16px;

  display: flex;
  align-items: center;

  color: #929292;
}
</style>
