<script setup lang='ts'>
import { computed } from 'vue'
import { NModal } from 'naive-ui'

interface Props {
  visible: boolean
}

interface Emit {
  (e: 'update:visible', visible: boolean): void
}

const props = defineProps<Props>()

const emit = defineEmits<Emit>()

const show = computed({
  get: () => props.visible,
  set: (visible: boolean) => emit('update:visible', visible),
})
</script>

<template>
  <NModal
    v-model:show="show"
    style="width: 90%; max-width: 900px"
    preset="card"
    :title="$t('setting.donate')"
  >
    <div class="p-4 space-y-4">
      <div
        class="p-2 space-y-2 rounded-md bg-neutral-100 dark:bg-neutral-700"
      >
        <p>
          如果您觉得我维护的服务对您有所帮助或启发，不妨请我喝一杯咖啡吧！您的慷慨将成为我继续维护和服务的动力。
        </p>
        <p>
          服务器和API需要消耗资源，捐赠是自愿的，即使您不进行捐赠，您也可以在运行期间自由地使用此服务。
        </p>
        <p>扫描这里，为我注入能量！谢谢您。</p>
      </div>
      <div class="flex gap-10 flex-col md:flex-col lg:flex-row">
        <div class="flex-1">
          <img src="@/assets/wechat.jpg" alt="WeChat">
        </div>
        <div class="flex-1">
          <img src="@/assets/alipay.jpg" alt="Alipay">
        </div>
      </div>
    </div>
  </NModal>
</template>
