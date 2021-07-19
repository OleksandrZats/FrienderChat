<template>
  <h3 class="HCHeader">Admin settings</h3>
  <label for="adminName"></label>
  <input
    class="nameInput"
    type="text"
    name="adminName"
    id="inputName"
    :placeholder="this.name"
    v-model="name"
    @input="onNameChange(name)"
  />
</template>
<script>
export default {
  data() {
    return { name: "" };
  },
  props: ["name"],
  methods: {
    onNameChange(name) {
      this.$emit("onNameChange", {
        name: name,
      });
    },
  },
};
</script>
<style>
.HCHeader {
  margin: 24px 24px 0 24px;
}
.nameInput {
  background: #f9f9f9;
  border: 1px solid #adb6c8;
  box-sizing: border-box;
  border-radius: 4px;
  padding: 8px 10px;

  font-size: 16px;
  line-height: 24px;
  margin: 24px;
}
</style>
