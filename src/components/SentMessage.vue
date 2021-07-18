<template>
  <div class="sentMessage" :style="'--sentMessageColor: ' + this.color">
    <p class="sentMessage__text" v-if="!messageText">
      Lorem ipsum dolor sit amet consectetur.
    </p>
    <p class="sentMessage__text" v-if="messageText">
      {{ messageText.message }}
    </p>
    <p class="sentMessage__time">6:64 PM</p>
  </div>
</template>

<script>
export default {
  props: ["color", "messageText"],
  data() {
    return {
      sentMessageColor: this.color,
    };
  },
  components: {},
};
</script>

<style>
.sentMessage {
  background-color: var(--sentMessageColor);
  border-radius: 8px;
  padding: 8px 16px;
  margin: 0 16px 16px 41px;
}

.sentMessage__text {
  font-size: calc(16px + var(--deltaFontSize));

  line-height: 24px;

  display: flex;
  align-items: center;

  color: #ffffff;
}

.sentMessage__time {
  font-size: calc(12px + var(--deltaFontSize));
  line-height: 16px;

  display: flex;
  align-items: center;

  color: #e0e0e0;
}
</style>
