<template>
  <div
    v-if="opened"
    class="fixed top-0 bottom-0 left-0 right-0 z-20 flex items-center justify-center bg-black bg-opacity-40"
    @click="close()"
  >
    <div
      class="max-h-[80%] max-w-[80%] relative z-30 p-5 border-2 opacity-100 border-neon-blue shadow-modal-neon-blue rounded-2xl"
    >
      <ModalCloseButton
        class="absolute top-0 right-0 transform origin-center translate-x-1/2 -translate-y-1/2"
        @click.native="close()"
      />
      <div
        class="border-2 border-neon-pink shadow-modal-neon-pink rounded-2xl"
        @click.stop=""
      >
        <div class="bg-gray-800 rounded-2xl">
          <slot name="content"> </slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'

export interface Modal {
  opened: boolean
}

export default defineComponent({
  props: {
    opened: { type: Boolean, required: true },
  },
  emits: ['close'],
  setup(_, { emit }) {
    const close = (): void => {
      emit('close')
    }
    return { close }
  },
})
</script>
