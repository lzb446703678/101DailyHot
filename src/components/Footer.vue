<template>
  <footer class="footer"> <!-- 应用居中样式 -->
    <div class="copyright">
      <n-text class="description" v-html="packageJson.description" />
      <n-text
        class="author"
        :depth="3"
        v-html="packageJson.author"
        @click="jumpLink(packageJson.github)"
      />
      <!-- 新增的段落 -->
      <n-text class="additional-info" :depth="3">
         基于
         <a href="https://github.com/imsyy" target="_blank">imsyy</a>
         的开源项目并遵循
         <a href="https://opensource.org/licenses/MIT" target="_blank">MIT许可协议</a>。
      </n-text>
    </div>
    <n-text
      v-if="icp"
      :depth="3"
      class="icp"
      v-html="icp"
      @click="jumpLink('https://beian.miit.gov.cn/')"
    />
  </footer>
</template>



<script setup>
import packageJson from "@/../package.json";

const icp = ref(import.meta.env.VITE_ICP ? import.meta.env.VITE_ICP : null);

// 链接跳转
const jumpLink = (url) => {
  window.open(url);
};
</script>

<style lang="scss" scoped>
footer {
  height: 100px;
  padding: 0 5vw;
  max-width: 1800px;
  margin: 20px auto 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  .copyright {
    margin-bottom: 4px;
    text-align: center;
    .description {
      &::after {
        content: "@ Copyright By";
        margin: 0 6px;
      }
    }
  }
  .author {
    cursor: pointer;
    transition: all 0.3s;
    &:hover {
      color: var(--n-code-text-color);
    }
  }
  .icp {
    font-size: 13px;
    cursor: pointer;
    transition: all 0.3s;
    &:hover {
      color: var(--n-code-text-color);
    }
  }
  .additional-info {
  display: block; /* 使内容独占一行并可以应用居中对齐 */
}
}
</style>
