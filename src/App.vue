<template>
  <div id="app">
    <Header
      :listContact="filteredList"
      @showModal="showModal"
      @changeTitle="ChangeT($event)"
    />
    <div v-if="listContact.length === 0">
      <EmptyList v-bind:listContact="filteredList" @showModal="showModal" />
    </div>
    <div v-else>
      <PhoneList :listContact="filteredList" />
    </div>

    <ModalInsert
      v-show="showModalInsert"
      @close="closeModal"
      v-bind:listContact="listContact"
    >
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
      filteredList: [],
      showModalInsert: false,
      showModalDelete: false,
      search: "",
    };
  },
  watch: {
    listContact: function () {
      this.filteredList = this.listContact;
    },
  },
  computed: {},
  methods: {
    showModal() {
      this.showModalInsert = true;
    },
    closeModal() {
      this.showModalInsert = false;
    },
    ChangeT(title) {
      this.search = title;
      let newArray = this.listContact;
      if (this.search) {
        newArray = this.listContact.filter((item) => {
          return this.search
            .toLowerCase()
            .split(" ")
            .every(
              (v) =>
                item.name.toLowerCase().includes(v) ||
                item.email.toLowerCase().includes(v)
            );
        });
      } else {
        newArray = this.listContact;
      }
      this.filteredList = newArray;
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
