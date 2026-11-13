<template>
  <!-- 社交链接 -->
  <div v-if="socialLinks.length" class="social">
    <div class="link">
      <a
        v-for="item in socialLinks"
        :key="item.name"
        :href="item.url || undefined"
        :target="item.url ? '_blank' : undefined"
        @click="!item.url && $event.preventDefault()"
        @mouseenter="socialTip = item.tip"
        @mouseleave="socialTip = '通过这里联系我吧'"
      >
        <!-- 图标组件（如 GithubOne） -->
        <component
          :is="iconMap[item.name]"
          v-if="iconMap[item.name]"
          class="icon i-icon"
          :size="28"
          theme="filled"
          fill="#ffffff"
        />
        <!-- 图标图片 -->
        <img v-else class="icon" :src="item.icon" height="24" alt="" />
      </a>
    </div>
    <span class="tip">{{ socialTip }}</span>
  </div>
</template>

<script setup>
import { GithubOne, Mail } from "@icon-park/vue-next";
import socialLinks from "@/assets/socialLinks.json";

// 社交链接提示
const socialTip = ref("通过这里联系我吧");

// 图标组件映射（按 name 匹配，未命中则回退到 icon 图片路径）
const iconMap = {
  Github: GithubOne,
  Email: Mail,
};
</script>

<style lang="scss" scoped>
.social {
  margin-top: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: 460px;
  width: 100%;
  height: 42px;
  padding: 0 14px;
  // 与 .cards 一致的玻璃底
  background-color: rgb(0 0 0 / 12%);
  -webkit-backdrop-filter: blur(6px) saturate(140%);
  backdrop-filter: blur(6px) saturate(140%);
  border-radius: 6px;
  box-shadow:
    inset 0 1px 0 rgb(255 255 255 / 12%),
    0 4px 16px rgb(0 0 0 / 10%);
  transform: scale(1);
  // 悬停只做弹性放大，不改变底色
  transition:
    transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);
  animation: fade 0.5s;
  @media (max-width: 840px) {
    max-width: 100%;
    justify-content: center;
  }

  &:hover {
    transform: scale(1.04);
  }

  .link {
    display: flex;
    align-items: center;

    a {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 34px;
      height: 34px;
      margin-right: 12px;
      transition: transform 0.3s;

      .icon {
        display: block;
        filter: drop-shadow(0 1px 4px rgb(0 0 0 / 45%));
      }

      &:hover {
        transform: scale(1.15);
      }

      &:active {
        transform: scale(0.95);
      }
    }
  }

  .tip {
    font-size: 0.9rem;
    color: rgb(255 255 255 / 70%);
    margin-right: 12px;
    white-space: nowrap;
    animation: fade 0.5s;
  }
}
</style>
