<template>
  <form class="form" @submit.prevent="onMessageSend(message)">
    <input
      type="text"
      class="form__input"
      placeholder="Your message..."
      v-model="message"
    />
    <button type="submit" class="form__submit">
      <img src="@/assets/Send.svg" alt="" />
    </button>
  </form>
</template>
<script>
export default {
  data() {
    return { message: "" };
  },
  methods: {
    onMessageSend(message) {
      this.$emit("onMessageSend", {
        message: message,
      });
      this.message = "";
    },
  },
};
</script>

<style>
.form {
  display: flex;
}
.form__input {
  flex-grow: 10;
  background: transparent;
  border: none;
  margin-left: 18px;
  margin: 20px 0px 20px 18px;
  font-size: 16px;
  line-height: 24px;
  padding: 10px 8px;
}
.form__input::placeholder {
  font-size: 16px;
  line-height: 24px;

  color: #adb6c8;
}
.form__submit {
  background: transparent;
  border: none;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 20px 18px;
}
.form__submit img {
  width: 20px;
  height: 20px;
}
</style>
