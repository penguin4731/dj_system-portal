<template>
  <div class="flex flex-col items-center content-center">
    <img width="200px" height="200px" :src="url" :alt="`${roomName} Logo`" />
    <p class="mt-5 text-4xl">{{ roomName }}</p>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from '@vue/composition-api'

export interface RoomLogo {
  roomName: string
  imageUrl: string
}

export default defineComponent({
  props: {
    roomName: { type: String, required: true },
    imageUrl: { type: String, required: true },
  },
  setup(props: RoomLogo) {
    const url = computed((): string =>
      props.imageUrl
        ? props.imageUrl
        : require('@/assets/img/default_room_logo.png')
    )
    return {
      url,
    }
  },
})
</script>
