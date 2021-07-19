<template>
  <div class="customizeComponent">
    <div class="menu">
      <ul>
        <li v-for="tab in tabs" :key="tab">
          <button
            type="button"
            class="menu__link"
            @click="setActive(tab)"
            :class="{ active: isActive(tab) }"
          >
            {{ tab }}
          </button>
        </li>
      </ul>
    </div>
    <div class="customizer">
      <div
        id="colors"
        class="tab"
        v-bind:class="{ tabActive: isActive('colors') }"
      >
        <ChatColors
          :colors="this.colors"
          @changeClr="changeClr"
          :chatColor="this.chatColor"
        />
      </div>
      <div
        id="fonts"
        class="tab"
        v-bind:class="{ tabActive: isActive('fonts') }"
      >
        <ChatFonts
          :fonts="this.fonts"
          :chatFont="this.chatFont"
          @changeFnt="changeFnt"
        />

        <label class="inputRangeLable" for="size"
          >Size change : {{ size }}px</label
        >
        <input
          class="inputRange"
          type="range"
          id="size"
          name="size"
          min="-10"
          max="10"
          step="0.5"
          v-model.number="size"
          @input="onChangeSize(size)"
        />
      </div>
      <div
        id="header"
        class="tab"
        v-bind:class="{ tabActive: isActive('header') }"
      >
        <HeaderCustomize @onNameChange="onNameChange" :name="name" />
      </div>
    </div>
  </div>
</template>

<script>
import ChatColors from "@/components/ChatColors";
import ChatFonts from "@/components/ChatFonts";
import HeaderCustomize from "@/components/HeaderCustomize";
export default {
  data() {
    return {
      activeItem: "",
      size: 0,
      tabs: ["colors", "fonts", "header"],
    };
  },
  mounted() {
    if (localStorage.activeItem) {
      this.activeItem = localStorage.activeItem;
    } else {
      this.activeItem = "colors";
    }
  },
  watch: {
    activeItem(newVctiveItem) {
      localStorage.activeItem = newVctiveItem;
    },
  },
  props: ["colors", "chatColor", "fonts", "chatFont", "name"],
  methods: {
    isActive(menuItem) {
      return this.activeItem === menuItem;
    },
    setActive(menuItem) {
      this.activeItem = menuItem;
    },
    changeClr(clr) {
      this.$emit("changeColor", {
        color: clr.color,
      });
    },
    changeFnt(fnt) {
      this.$emit("changeFnt", {
        font: fnt.font,
      });
    },
    onChangeSize(size) {
      this.$emit("onChangeSize", {
        size: size,
      });
    },
    onNameChange(name) {
      this.$emit("onNameChange", {
        name: name.name,
      });
    },
  },
  components: { ChatColors, ChatFonts, HeaderCustomize },
};
</script>

<style>
.customizeComponent {
  display: flex;
  flex-direction: row;
  border-top: 2px solid #eaeaeb;
  box-shadow: 0px 0px 22px rgba(0, 0, 0, 0.11);
}
.menu__link {
  padding: 12px 16px;
  background: #fff;
  min-width: 200px;
  border: none;
  cursor: pointer;
  text-align: start;
  border-radius: 8px;

  text-transform: capitalize;
}
.active {
  background: #3b5a9c;

  color: #fff;
}
.tab {
  display: none;
  flex-direction: column;
}
.tabActive {
  display: flex;
}
.menu {
  min-width: 258px;
  min-height: 640px;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  border-right: 2px solid #eaeaeb;
  margin-top: 24px;
}
li {
  list-style: none;
}
.customizer {
  border-right: 2px solid #eaeaeb;
  width: 320px;
}
.inputRange {
  justify-self: flex-end;
  margin: 0 24px;
}
.inputRangeLable {
  font-family: Inter;
  font-weight: 600;
  font-size: 16px;
  line-height: 24px;
  width: 100%;
  margin-bottom: 16px;
  margin-left: 24px;
}
/* input[type="range"]::-webkit-slider-thumb {
  position: relative;
}
input[type="range"]::-webkit-slider-thumb::before {
  position: absolute;
  top: -20px;
  content: ;
} */
</style>
