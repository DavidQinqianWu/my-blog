<template>
  <p>下面是 Custom 组件</p>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
  <br />

  <p>子组件inject 取值</p>
  <slot></slot>
  <h3 :style="{ color: theme.color }">我是子组件inject拿到颜色</h3>
  <h3 :style="{ color: theme1.color }">
    我是子组件injecct from theme的 theme1拿到颜色
  </h3>

  <!-- <h3 :style="{ color: injections.background.color }">
    我是函数式的组件来取得值
  </h3> -->
</template>
<script>
export default {
  name: "Custom",
  props: ["modelValue"],
  inject: {
    theme: {},
    theme1: {
      from: "theme",
      default: () => ({}),
    },
    // background: {
    //   default: () => ({})
    // }
  },
};
</script>
<style></style>
