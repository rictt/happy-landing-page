<template>
  <div class="component-list-wrapper">
    <div class="category-wrapper basic">
      <p class="category-title">基础组件</p>
      <div class="category-component-wrapper">
        <div
          class="component-item"
          v-for="(com, i) in basicList"
          :key="i"
          @click="onCompClick(com)"
        >
          <img class="component-item-icon" :src="com.iconSrc" alt="" />
          <p class="component-item-text">{{ com.label }}</p>
        </div>
      </div>
    </div>
    <div class="category-wrapper business">
      <p class="category-title">业务组件</p>
      <div class="category-component-wrapper">敬请期待</div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { BasicComponents } from "./data.js";

export default defineComponent({
  components: {},
  setup(props, ctx) {
    const basicList = ref(BasicComponents);
    const onCompClick = (comp) => {
      // 传递需要拷贝一下，不然同一批次创建的组件会对象引用
      const result = JSON.parse(JSON.stringify(comp));
      ctx.emit("add-component", result);
    };
    return {
      basicList,
      onCompClick,
    };
  },
});
</script>

<style lang="stylus" scoped>
@import "~@/style/variables.styl"
.component-list-wrapper {
  width: 300px;
  background-color: #fff;
  height: 100%;
  min-height: 667px;
  overflow: auto;
  box-sizing: border-box;
  padding: 10px;
  scrollBar();
}

.category-wrapper {
  text-align: left;
  padding: 8px 0;

  .category-title {
    font-size: 16px;
    padding-bottom: 10px;
    border-bottom: 1px solid #f2f2f2;
  }
}

.category-component-wrapper {
  display: flex;
  flex-wrap: wrap;
  .component-item {
    width: 33%;
    text-align: center;
    margin-bottom: 10px;
    cursor pointer

    .component-item-icon {
      width: 60%;
      margin: 0 auto;
    }

    .component-item-text {
      margin-top: 10px;
      font-size: 12px;
      color: #666;
    }
  }
}
</style>
