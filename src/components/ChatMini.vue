<template>
  <button type="button" class="them_button" @click="changeClr(this.color)">
    <div
      class="miniatureChat"
      :class="{ activeMini: this.chatColor == this.color }"
      :style="'--colorBorder: ' + this.color"
    >
      <svg
        width="58"
        height="77"
        viewBox="0 0 58 77"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect width="57.1429" height="76.8413" rx="4" fill="white" />
        <path
          d="M0 4C0 1.79086 1.79086 0 4 0H53.1429C55.352 0 57.1429 1.79086 57.1429 4V15.3683H0V4Z"
          :fill="color"
        />
        <rect
          x="3.80957"
          y="19.0127"
          width="35.2381"
          height="10"
          rx="2"
          fill="#F1F1F1"
        />
        <rect
          x="7.80957"
          y="21.0127"
          width="21"
          height="2"
          rx="1"
          fill="#ADB6C8"
        />
        <rect
          x="7.80957"
          y="25.0127"
          width="10"
          height="2"
          rx="1"
          fill="#ADB6C8"
        />
        <rect
          x="18.0947"
          y="32.46"
          width="35.2381"
          height="10"
          rx="2"
          :fill="color"
        />
        <rect x="22.0947" y="34.46" width="14" height="2" rx="1" fill="white" />
        <rect x="22.0947" y="38.46" width="24" height="2" rx="1" fill="white" />
        <rect
          x="3.80957"
          y="44.9473"
          width="35.2381"
          height="10"
          rx="2"
          fill="#F1F1F1"
        />
        <rect
          x="7.80957"
          y="46.9473"
          width="29"
          height="2"
          rx="1"
          fill="#ADB6C8"
        />
        <rect
          x="7.80957"
          y="50.9473"
          width="18"
          height="2"
          rx="1"
          fill="#ADB6C8"
        />
        <rect
          x="44.7617"
          y="65.3154"
          width="7.61905"
          height="7.68412"
          rx="2"
          :fill="color"
        />
        <rect
          x="3.80957"
          y="65.3154"
          width="37.1429"
          height="7.68412"
          rx="2"
          fill="#E1E3E7"
        />
      </svg>
    </div>
  </button>
</template>

<script>
export default {
  props: ["color", "chatColor"],
  methods: {
    changeClr(clr) {
      this.$emit("changeClr", {
        color: clr,
      });
    },
  },
};
</script>
<style>
.miniatureChat {
  padding: 14px;
  background: #f1f1f1;
  border: 2px solid #fff;
  border-radius: 8px;
}
.activeMini {
  border-color: var(--colorBorder);
}
.them_button {
  background: #fff;
  border: none;
  cursor: pointer;
}
</style>
