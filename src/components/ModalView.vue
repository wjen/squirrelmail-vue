<template>
  <div class="modal">
    <div class="overlay" @click="emit('closeModal')"></div>
    <div class="modal-card">
      <slot />
    </div>
  </div>
</template>

<script>
import useKeydown from "../composables/use-keydown";

export default {
  setup(props, { emit }) {
    /* Press Escape key to leave modal in addition to clicking outside of modal */
    useKeydown([
      {
        key: "Escape",
        fn: () => {
          emit("closeModal");
        }
      }
    ]);
    return {
      emit
    };
  }
};
</script>

<style></style>
