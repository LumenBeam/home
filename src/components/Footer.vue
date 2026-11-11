<template>
  <footer id="footer" :class="store.footerBlur ? 'blur' : null">
    <div class="power">
      <span>
        Copyright&nbsp;&copy;
        <span v-if="startYear && startYear !== fullYear" class="site-start">
          {{ startYear }}
          -
        </span>
        {{ fullYear }}
        <a :href="siteUrl">{{ siteAnthor }}</a>
      </span>
      <!-- 以下信息请不要修改哦 -->
      <span class="hidden">
        &amp;&nbsp;Made&nbsp;by
        <span>{{ config.author }}</span>
      </span>
      <!-- 站点备案 -->
      <a v-if="siteIcp" href="https://beian.miit.gov.cn" target="_blank">
        &amp;
        {{ siteIcp }}
      </a>
    </div>
  </footer>
</template>

<script setup>
import { mainStore } from "@/store";
import config from "@/../package.json";

const store = mainStore();
const fullYear = new Date().getFullYear();

// 加载配置数据
const siteStartDate = ref(import.meta.env.VITE_SITE_START);
// 建站年份（仅用于与当前年份不同时显示)
const startYear = computed(() =>
  siteStartDate.value?.length >= 4 ? Number(siteStartDate.value.substring(0, 4)) : null,
);
const siteIcp = ref(import.meta.env.VITE_SITE_ICP);
const siteAnthor = ref(import.meta.env.VITE_SITE_ANTHOR);
const siteUrl = computed(() => {
  const url = import.meta.env.VITE_SITE_URL;
  if (!url) return "#";
  // 判断协议前缀
  if (!url.startsWith("http://") && !url.startsWith("https://")) {
    return "//" + url;
  }
  return url;
});
</script>

<style lang="scss" scoped>
#footer {
  width: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  height: 46px;
  line-height: 46px;
  text-align: center;
  z-index: 0;
  font-size: 14px;
  .power {
    animation: fade 0.3s;
  }
  &.blur {
    backdrop-filter: blur(10px);
    background: rgb(0 0 0 / 25%);
    font-size: 16px;
  }
  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 0.15s ease-in-out;
  }
  @media (max-width: 720px) {
    font-size: 0.85rem;
    &.blur {
      font-size: 0.85rem;
    }
  }
  @media (max-width: 480px) {
    .hidden {
      display: none;
    }
  }
}
</style>
