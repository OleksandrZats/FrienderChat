<template>
  <div class="chatHeader" :style="'--headerColor: ' + this.color">
    <img src="@/assets/Photo.png" alt="Photo" class="chatHeader__photo" />
    <div class="chatHeader__text">
      <h2 class="chatHeader__name">{{ this.name }}</h2>
      <p class="chatHeader__role">Support</p>
    </div>
    <button class="chatHeader__arrow">
      <img src="@/assets/Vector.svg" alt="" />
    </button>
  </div>
</template>

<script>
export default {
  props: ["color", "name"],
  data() {
    return {
      headerColor: this.color,
    };
  },
  components: {},
};
</script>

<style>
.chatHeader {
  background: var(--headerColor);
  border-radius: 16px 16px 0px 0px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 16px 33px 16px 16px;
  color: #fff;
  margin-bottom: 24px;
}
.chatHeader__text {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  margin: 0 0 0 8px;
  flex-grow: 10;
}
.chatHeader__name {
  font-weight: bold;
  font-size: calc(16px + var(--deltaFontSize));
  line-height: calc(24px + var(--deltaFontSize));
}
.chatHeader__role {
  font-size: calc(12px + var(--deltaFontSize));
  line-height: calc(16px + var(--deltaFontSize));
}
.chatHeader__arrow {
  background: transparent;
  outline: none;
  border: none;
  cursor: pointer;
  font-size: 20px;
  font-weight: 900;

  color: #fff;
}
</style>
