<template>
  <div class="wrapper">
    <div class="leftSide">
      <ChatCustomizer
        @changeColor="changeColor"
        @changeFnt="changeFnt"
        @onChangeSize="onChangeSize"
        @onNameChange="onNameChange"
        :colors="colors"
        :chatColor="color"
        :fonts="fonts"
        :chatFont="font"
        :name="name"
      />
    </div>
    <div class="chatEditor">
      <ChatTemplate
        :color="color"
        :font="font"
        :deltaFont="deltaFont"
        :name="name"
      />
    </div>
    <button type="button" class="lsClear" @click="onClearLC()">
      Clear Local Storage
    </button>
  </div>
</template>

<script>
import ChatCustomizer from "@/components/ChatCustomizer";
import ChatTemplate from "@/components/ChatTemplate";

export default {
  data() {
    return {
      color: "",
      colors: [
        "#3B5A9C",
        "#4EB2A9",
        "#A44EB2",
        "#D9A159",
        "#4EA0B2",
        "#AAE287",
        "#B493DE",
        "#72A2FF",
      ],
      font: "",
      fonts: ["Inter", "Roboto", "Open Sans", "Merriweather"],
      deltaFont: 0,
      name: "Name Surname",
    };
  },
  mounted() {
    if (localStorage.color) {
      this.color = localStorage.color;
    } else {
      this.color = "#A44EB2";
    }
    if (localStorage.font) {
      this.font = localStorage.font;
    } else {
      this.font = "Roboto";
    }
    if (localStorage.deltaFont) {
      this.deltaFont = localStorage.deltaFont;
    } else {
      this.deltaFont = 0;
    }
    if (localStorage.name) {
      this.name = localStorage.name;
    } else {
      this.name = "Name Surname";
    }
  },
  watch: {
    color(newColor) {
      localStorage.color = newColor;
    },
    font(newFont) {
      localStorage.font = newFont;
    },
    deltaFont(newDeltaFont) {
      localStorage.deltaFont = newDeltaFont;
    },
    name(newName) {
      localStorage.name = newName;
    },
  },
  methods: {
    changeColor(newColor) {
      this.color = newColor.color;
    },
    changeFnt(newFnt) {
      this.font = newFnt.font;
    },
    onChangeSize(newSize) {
      this.deltaFont = newSize.size;
    },
    onNameChange(newName) {
      this.name = newName.name;
    },
    onClearLC() {
      localStorage.clear();
      window.location.reload();
    },
  },
  name: "App",
  components: { ChatTemplate, ChatCustomizer },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700;900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700;900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Merriweather:wght@400;700;900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.wrapper {
  display: flex;
}
.leftSide {
  font-family: Inter;
  width: 580px;
}
.chatEditor {
  padding-left: 189px;
  padding-top: 24px;
}
.lsClear {
  position: fixed;
  top: 20px;
  right: 20px;
  background-color: transparent;
  border-radius: 8px;
  padding: 4px;
  font-size: 16px;
  font-weight: bold;
  border: 4px solid red;
}
</style>
