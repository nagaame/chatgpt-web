<script setup lang='ts'>
import { onMounted, ref } from 'vue'
import { NSpin } from 'naive-ui'
import { fetchChatConfig } from '@/api'

interface ConfigState {
  timeoutMs?: number
  reverseProxy?: string
  apiModel?: string
  socksProxy?: string
}

const loading = ref(false)

const config = ref<ConfigState>()

async function fetchConfig() {
  try {
    loading.value = true
    const { data } = await fetchChatConfig<ConfigState>()
    config.value = data
  }
  finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchConfig()
})
</script>

<template>
  <NSpin :show="loading">
    <div class="p-4 space-y-4">
      <div class="p-2 space-y-2 rounded-md bg-neutral-100 dark:bg-neutral-700">
        <p>
          如果您觉得我维护的服务对您有所帮助或启发，不妨请我喝一杯咖啡吧！您的慷慨将成为我继续维护和服务的动力。
        </p>
        <p>
          扫描这里，为我注入能量！谢谢您。
        </p>
      </div>
      <div class="flex gap-10 flex-col md:flex-col lg:flex-row">
        <div class="flex-1">
          <img src="../../../assets/wechat.jpg" alt="WeChat">
        </div>
        <div class="flex-1">
          <img src="../../../assets/alipay.jpg" alt="Alipay">
        </div>
      </div>
    </div>
  </NSpin>
</template>
