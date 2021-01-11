<template>
  <div class="modal-overlay" v-if="isOpen" @click="closeEvent">
    <div
      class="modal"
      @click="
        (e) => {
          e.preventDefault();
        }
      "
    >
      <div class="close-btn" v-if="showDefaultCloseBtn" @click="onRequestClose">
        &times;
      </div>
      <div class="modal-body">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "VueModal",
  props: {
    // Required; specifies whether
    // or not the modal should be shown (open)
    isOpen: {
      type: Boolean,
      required: true,
    },
    // Called when user tries to exit the modal by
    // either clicking the modal-overlay or the
    // default close button
    onRequestClose: {
      type: Function,
      required: true,
    },
    // only optional prop; specifies whether
    // or not the default close button
    // in the top right should be shown.
    showDefaultCloseBtn: {
      type: Boolean,
      default: true,
    },
  },
  methods: {
    closeEvent(e) {
      // we check the target to ensure that
      // the user clicked the actual modal-overlay,
      // not a child in the element.
      if (e.target.className !== "modal-overlay") return;

      // then, call the requestClose prop passed into the modal
      this.onRequestClose();
    },
  },
};
</script>

<style>
.close-btn {
  position: absolute;
  top: 0;
  right: 0;
  padding: 0.5rem;
  height: 1rem;
  line-height: 1rem;
  width: 1rem;
  opacity: 0.8;
  transition: all 0.2s;
  font-size: 1rem;
  text-align: center;
}

.close-btn:hover {
  cursor: pointer;
  opacity: 1;
}

.modal-overlay {
  position: fixed;
  z-index: 100;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  transition: opacity 0.3s;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-enter,
.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  transform: scale(1.1);
}

.modal {
  width: 300px;
  height: 40%;
  padding: 1rem;
  background-color: #fff;
  border-radius: 5px;
  transition: all 0.2s;
  box-shadow: 0 0 8px 3px rgba(30, 30, 30, 0.3);
  position: relative;
  z-index: 101;
}
</style>