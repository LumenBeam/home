<template>
  <div class="box" @click="store.boxOpenState = false">
    <div class="content">
      <!-- 可在此处自定义任意内容 -->
      <TimeCapsule />
      <MoreContent />
    </div>
  </div>
</template>

<script setup>
import { mainStore } from "@/store";
import TimeCapsule from "@/components/TimeCapsule.vue";
import MoreContent from "@/components/MoreContent.vue";

const store = mainStore();
</script>

<style lang="scss" scoped>
.box {
  flex: 1 0 0%;
  margin-left: 0.75rem;
  height: 80%;
  max-width: 50%;
  position: relative;
  animation: fade 0.5s;
  cursor: pointer;
  // 玻璃容器样式
  border-radius: 6px;
  background-color: rgb(0 0 0 / 12%);
  -webkit-backdrop-filter: blur(6px) saturate(140%);
  backdrop-filter: blur(6px) saturate(140%);
  box-shadow:
    inset 0 1px 0 rgb(255 255 255 / 12%),
    0 4px 16px rgb(0 0 0 / 10%);
  transform: scale(1);
  // 弹性缓动，与其它卡片保持一致
  transition: transform 0.35s cubic-bezier(0.34, 1.56, 0.64, 1);

  &:hover {
    transform: scale(1.03);
  }
  &:active {
    transform: scale(0.98);
  }

  .content {
    display: flex;
    flex-direction: column;
    padding: 30px;
    width: 100%;
    height: 100%;
  }
}
</style>
