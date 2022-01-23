<template>
  <div id="app">
    <Header v-bind:listContact="listContact" @showModal="showModal" />
    <div v-if="listContact.length === 0">
      <EmptyList v-bind:listContact="listContact" @showModal="showModal" />
    </div>
    <div v-else>
      <PhoneList v-bind:listContact="listContact" />
    </div>

    <ModalInsert
      v-show="showModalInsert"
      @close="closeModal"
      v-bind:listContact="listContact"
    >
      <template v-slot:header> This is a new modal header. </template>

      <template v-slot:body> This is a new modal body. </template>

      <template v-slot:footer> This is a new modal footer. </template>
    </ModalInsert>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ModalInsert from "./components/ModalInsert.vue";
import PhoneList from "./components/PhoneList.vue";
import EmptyList from "./components/EmptyList.vue";

export default {
  name: "App",
  data() {
    return {
      contact: {
        id: 1,
        name: "",
        email: "",
        phone: "",
      },
      listContact: [],
      showModalInsert: false,
      showModalDelete: false,
    };
  },
  methods: {
    showModal() {
      this.showModalInsert = true;
    },
    closeModal() {
      this.showModalInsert = false;
    },
    showModalDeleteFunc() {
      this.showModalDelete = true;
    },
    closeModalDeleteFunc() {
      this.showModalDelete = false;
    },
  },
  components: {
    Header,
    ModalInsert,
    PhoneList,
    EmptyList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  background-color: #f8f9fd;
  padding: 0 16px;
}
</style>
