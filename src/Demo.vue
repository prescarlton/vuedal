<template>
  <div id="app">
    <h1>Vuedal Demo</h1>

    <VueModal :isOpen="showModal" :onRequestClose="closeModal">modal! woo!</VueModal>
    <button @click="openModal">show</button>
  </div>
</template>

<script>
import VueModal from '@/components/Modal';

export default {
  name: "App",
  components: {
      VueModal
  },
  data: function() {
      return {
          showModal: false
      }
  },
  methods: {
      openModal: function(){
          this.showModal = true;
      },
      closeModal: function(){
          this.showModal = false;
      }
  }

};
</script>

<style>
</style>