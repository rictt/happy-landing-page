<template>
  <div class="color-picker-wrap">
    <a-input class="color-picker-input" v-model:value="color" allowClear />
    <input
      ref="colorInput"
      class="color-picker-select"
      type="color"
      v-model="color"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import useModelValue from "@/hooks/useModelValue";

export default defineComponent({
  name: "happy-color-picker",
  props: {
    modelValue: {
      type: String,
      default: "",
    },
  },
  setup(props, ctx) {
    const { color } = useModelValue({
      props,
      ctx,
      valueKey: "color",
      propsKey: "modelValue",
    });
    // const state = reactive({
    //   color: props.modelValue,
    // });

    // watch(
    //   () => props.modelValue,
    //   (val) => {
    //     state.color = val;
    //   }
    // );

    // watch(
    //   () => state.color,
    //   (val) => {
    //     ctx.emit("update:modelValue", val);
    //   }
    // );

    return {
      // ...toRefs(state),
      color,
    };
  },
});
</script>

<style lang="stylus" scoped>
.color-picker-wrap {
  display: flex;
  align-items: center;

  .color-picker-input {
    width: 50%;
    margin-right: 20px;
  }
  .color-picker-select {
  }
}
</style>
