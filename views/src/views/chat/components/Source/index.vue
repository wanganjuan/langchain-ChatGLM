<script setup lang='ts' name="source">
import { computed, ref } from 'vue'
import { NModal } from 'naive-ui'
import TextComponent from '../Message/Text.vue'
interface Props {
  dialogTag: boolean
  source: any
}

interface Emit {
  (e: 'close', visible: boolean): void
}
const props = defineProps<Props>()

const emit = defineEmits<Emit>()

const dialog = computed({
  get() {
    return props.dialogTag 
  },
  set(visible: boolean) {
    emit('close', visible)
  },
})
</script>

<template>
  <NModal v-model:show="dialog" preset="dialog" title="数据来源" style="width: 95%; max-width: 640px">

    <div v-for="(item, index) in source" :key="index">
      <TextComponent :text="item" />
    </div>
  
  </NModal>
</template>
