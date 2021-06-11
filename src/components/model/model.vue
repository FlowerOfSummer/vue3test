<template>
  <Teleport to="body" :disabled="isTeleport">
    <div class="modal">
      <div
        class="mask"
      ></div>
      <div class="modal__main">
        <div class="modal__title line line--b">
          <span>{{ title }}</span>
          <span class="close"  >✕</span
          >
        </div>
        <div class="modal__content">
          <Content v-if="typeof content === 'function'" :render="content" />
          <slot v-else>
            {{ content }}
          </slot>
        </div>
        <div class="modal__btns line line--t">
          <button :disabled="loading" @click="handleConfirm">
            <span class="loading" v-if="loading"> ❍ </span>{{ t("r.confirm") }}
          </button>
          <button @click="!loading && handleCancel()">
            {{ t("r.cancel") }}
          </button>
        </div>
      </div>
    </div>
  </Teleport>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    isTeleport: {
      type: Boolean,
      required: true,
    },
    title: {
      type: String
    },
    content: {
      type: Function || String
    }
  },
  setup() {},
});
</script>
