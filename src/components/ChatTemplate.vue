<template>
  <div class="template">
    <transition name="fade">
      <div
        class="chat"
        v-if="isFlex"
        :style="
          '--font: ' + this.font + '; --deltaFontSize: ' + this.deltaFont + 'px'
        "
      >
        <ChatHeader
          :color="this.color"
          :name="this.name"
          @onArowClick="
            () => {
              isFlex = !isFlex;
            }
          "
        />
        <div class="chat__messeges">
          <ReceiveMessage />
          <SentMessage :color="this.color" />
          <ReceiveMessage />
          <div v-for="message in messages" v-bind:key="message">
            <SentMessage :color="this.color" :messageText="message" />
          </div>
        </div>
        <ChatForm @onMessageSend="onMessageSend" />
      </div>
    </transition>
    <button
      type="button"
      class="chatButton"
      :style="'--buttonColor: ' + this.color"
      @click="
        () => {
          isFlex = !isFlex;
        }
      "
    >
      <img src="@/assets/Chat.svg" alt="" />
    </button>
  </div>
</template>

<script>
import ChatHeader from "@/components/ChatHeader";
import ReceiveMessage from "@/components/ReceiveMessage";
import SentMessage from "@/components/SentMessage";
import ChatForm from "@/components/ChatForm";

export default {
  data() {
    return {
      isFlex: true,
      messages: [],
    };
  },
  props: ["color", "font", "deltaFont", "photo", "name"],
  components: { ChatHeader, ReceiveMessage, SentMessage, ChatForm },
  name: "ChatTemplate",
  methods: {
    onMessageSend(message) {
      this.messages.push(message);
    },
  },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
.template {
  display: flex;
  position: absolute;
}
.chat {
  width: 380px;
  background: #fafafa;
  box-shadow: 0px 8px 28px rgba(3, 12, 31, 0.12);
  border-radius: 16px;
  min-height: 640px;
  display: flex;
  flex-direction: column;
  font-family: var(--font);
}
.chat__messeges {
  flex-grow: 10;
}
.chatButton {
  background: var(--buttonColor);
  box-shadow: 0px 8px 22px rgba(0, 0, 0, 0.11);
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 72px;
  height: 72px;
  border: none;
  cursor: pointer;
  align-self: flex-end;
  position: fixed;
  top: 620px;
  left: 1140px;
  margin-left: 32px;
}
.chatButton::before {
  content: " ";
  position: absolute;
  left: -10%;
  right: -10%;
  top: -10%;
  bottom: -10%;

  opacity: 0.65;
  /* Blue */

  border: 1px solid var(--buttonColor);
  box-sizing: border-box;
  border-radius: 50%;
}
.chatButton::after {
  content: " ";
  position: absolute;
  left: -20%;
  right: -20%;
  top: -20%;
  bottom: -20%;

  opacity: 0.22;
  /* Blue */

  border: 1px solid var(--buttonColor);
  box-sizing: border-box;
  border-radius: 50%;
}
</style>
