<template>
  <div id="phone-list">
    <div class="header_table">
      <div class="title_header contact_title">Contatos</div>
      <div class="title_header item_header">E-mail</div>
      <div class="title_header item_header-phone">Telefone</div>
    </div>
    <span class="container_list">
      <div
        id="phone"
        v-for="(phone, index) in listContact"
        v-bind:key="phone.id"
        :class="[phone.last === true ? 'new_item' : 'item_list']"
      >
        <div
          id="circle"
          class="col_circle circle"
          :style="{ backgroundColor: getColor(index) }"
        >
          {{ getLetter(phone) }}
        </div>
        <div id="name" class="name item_name">{{ phone.name }}</div>
        <div id="email" class="name item_header">{{ phone.email }}</div>
        <div id="phone" class="name item_header-phone-list">
          {{ phone.phone }}
        </div>
        <span class="container_buttons">
          <div class="col_none">
            <img
              src="../assets/ic-edit.png"
              class="edit-button"
              alt="pic"
              id="img"
              v-on:click="showModalEditFunc(phone.id)"
            />
          </div>
          <div class="col_none">
            <img
              src="../assets/ic-delete.png"
              class="edit-button"
              alt="pic"
              id="img"
              v-on:click="showModalDeleteFunc(phone.id)"
            />
          </div>
        </span>
        <ModalDelete
          v-show="selectedIdDelete === phone.id"
          @close="closeModalDeleteFunc"
          v-bind:key="phone.id"
          :listContact="listContact"
          :phoneId="index"
        >
        </ModalDelete>
        <ModalEdit
          v-show="selectedId === phone.id"
          @close="closeModalEditFunc"
          v-bind:key="phone.id"
          :listContact="listContact"
          :phoneId="index"
        >
        </ModalEdit>
      </div>
    </span>
  </div>
</template>

<script>
import ModalDelete from "./ModalDelete";
import ModalEdit from "./ModalEdit.vue";

export default {
  name: "list",
  props: ["listContact"],
  data() {
    return {
      showModalDelete: false,
      showModalEdit: false,
      selectedId: -1,
      selectedIdDelete: -1,
      colorCache: {},
    };
  },
  methods: {
    delete() {
      this.$emit("close");
    },
    edit() {
      let teste = this.listContact.push({
        id: this.listContact.length + 1,
        name: "",
        email: "",
        phone: 1,
      });
      this.listContact = teste;
      this.$emit("close");
    },
    showModalDeleteFunc(value) {
      this.selectedIdDelete = value;
    },
    closeModalDeleteFunc() {
      this.selectedIdDelete = -1;
    },
    showModalEditFunc(value) {
      this.selectedId = value;
    },
    closeModalEditFunc() {
      this.selectedId = -1;
    },
    getColor(idPhone) {
      const r = () => Math.floor(256 * Math.random());

      return (this.colorCache[idPhone] = `rgb(${r()}, ${r()}, ${r()})`);
    },
    getLetter(phone) {
      return phone.name.charAt(0).toLowerCase();
    },
    onClick(number) {
      this.idToEdit = number;
    },
  },
  components: {
    ModalDelete,
    ModalEdit,
  },
};
</script>

<style scoped>
.header_table {
  width: 100%;
  height: 40px;
  margin: 16px 0px 1px 0px;
  border-radius: 4px;
  border: solid 1px #e1e1e1;
  background-color: #fff;
  display: flex;
  justify-content: left;
}
.title_header {
  color: #9198af;
  display: flex;
  justify-content: left;
  align-items: center;
  min-width: 300px;
}

.title_header-none-image {
  color: #9198af;
  width: 24px;
  margin-right: 16px;
}

.item_name {
  width: 300px;
}

.title_header-none {
  flex-basis: 20%;
}

.contact_title {
  float: left;
  margin-left: 47px;
}

.item_header {
  margin-left: 175px;
}

.item_header-phone {
  margin-left: 215px;
}

.item_header-phone-list {
  margin-left: 215px;
}

.edit-button {
  cursor: pointer;
  padding: 0px 16px;
}

.item_phone {
  display: flex;
  flex-wrap: wrap;
}

.item_list {
  width: 100%;
  margin: 0px 0px 1px 0px;
  padding: 8px 0px 8px 0px;
  border-radius: 4px;
  border: solid 1px #e1e1e1;
  background-color: #ffffff;
  display: flex;
}

.container_list {
  max-height: 40px;
}

.new_item {
  width: 100%;
  margin: 0px 0px 1px 0px;
  padding: 8px 0px 8px 0px;
  border-radius: 4px;
  border: solid 1px #e1e1e1;
  background-color: #ffffff;
  display: flex;
  background: #ffffff;
  animation: mymove 10s;
}

@keyframes mymove {
  from {
    background-color: #fff3f2;
  }
  to {
    background-color: #ffffff;
  }
}

.item_list:hover {
  background-color: #fff3f2;
}

.new_item:hover {
  background-color: #fff3f2;
}

.circle {
  height: 24px;
  width: 24px;
  background-color: #bbb;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 16px;
  font-weight: 500;
  color: #fff;
}

.container_buttons {
  right: 16px;
  display: flex;
  position: absolute;
}

.col_circle {
  width: 25px;
  margin-right: 16px;
  margin-left: 8px;
}

.name {
  display: flex;
  justify-content: left;
  align-self: center;
  flex-wrap: wrap;
  min-width: 300px;
}
</style>
