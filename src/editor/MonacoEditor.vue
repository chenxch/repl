<script setup lang="ts">
import Monaco from '../monaco/Monaco.vue'
import type { PreviewMode } from './types'

defineProps<{
  value: string
  filename: string
  readonly?: boolean
  mode?: PreviewMode
}>()

const emit = defineEmits<{
  (e: 'change', code: string): void
}>()

defineOptions({
  editorType: 'monaco',
})

const onChange = (code: string) => {
  emit('change', code)
}
</script>

<template>
  <Monaco
    @change="onChange"
    :filename="filename"
    :value="value"
    :readonly="readonly"
    :mode="mode"
  />
</template>
