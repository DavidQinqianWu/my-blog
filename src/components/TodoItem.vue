<template>
  <li>
    <input type="checkbox" v-model="checked" />
    <slot name="prefixIcon"></slot>
    <span>{{ value }}</span>
    <slot name="endIcon">😀</slot>
    <span>{{ title }}</span>
    <button v-show="!del" @click="handlClick">删除</button>
  </li>
</template>
<script>
export default {
  props: {
    title: String,
    del: {
      type: Boolean,
      default: false,
    },
  },

  methods: {
    handClick() {
      console.log("删除了");
      this.$emit("delete", this.item);
    },
  },
  data() {
    return {
      value: Math.random(),
    };
  },
};
</script>
<style lang=""></style>
