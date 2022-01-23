<script>
export default {
  name: "ModalInsert",
  props: ["listContact", "phoneId"],
  data() {
    return {
      id: "",
      name: "",
      email: "",
      phone: "",
      last: false,
    };
  },
  methods: {
    close() {
      this.phoneId = -1;
      this.$emit("close");
    },
    sendData() {
      console.log("this.phoneId", this.phoneId + 1);
      this.$emit("close");
      let newList = this.listContact;
      newList.splice(this.phoneId, 1);
      this.listContact = newList;
      this.$emit("close");
    },
  },
};
</script>

<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div
        class="modal_delete"
        role="dialog"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header class="modal_header-delete" id="modalTitle">
          <div name="header" class="header_delete">Excluir contato</div>
        </header>

        <section class="modal-body-delete" id="modalDescription">
          <div name="body" class="body">
            Deseja realmente excluir o contato?
          </div>
        </section>

        <footer class="modal-footer">
          <button
            type="button"
            class="btn_close-delete"
            @click="close"
            aria-label="Close modal"
          >
            Cancelar
          </button>

          <button
            type="button"
            class="btn-orange"
            @click="sendData"
            aria-label="Close modal"
          >
            Excluir
          </button>
        </footer>
      </div>
    </div>
  </transition>
</template>

<style>
.header_delete {
  width: 106px;
  height: 19px;
  margin: 0 260px 0px 16px;
  font-family: Roboto;
  font-size: 16px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #2a2d3b;
}

.body {
  color: #2a2d3b;
  font-family: Roboto;
  text-align: left;
  font-size: 14px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
}

.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal_delete {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  width: 432px;
  height: 207px;
  border-radius: 16px;
}

.modal-header,
.modal-footer {
  display: flex;
  flex-direction: row;
}

.modal_header-delete {
  position: relative;
  border-bottom: 1px solid #c0c3d2;
  justify-content: space-between;
  padding: 12.5px 0px !important;
}

.modal-footer {
  border-top: 1px solid #c0c3d2;
  flex-direction: column;
}

.modal-body-delete {
  position: relative;
  padding: 20px 24px 57px 24px;
}

.btn_close-delete {
  position: relative !important;
  width: 80px !important;
  top: 0;
  right: 0;
  background-color: transparent;
  font-family: Roboto;
  font-size: 16px;
  padding: 0px !important;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: center;
  box-shadow: none;
  margin: 0px 0px 0 60px !important;
  color: #fa7268 !important;
  cursor: pointer;
}

.btn-orange {
  width: 80px;
  height: 32px;
  margin: 1px 1px 1px 0;
  padding: 5px 5px;
  border-radius: 16px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #fa7268;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
  color: #ffffff;
}

.modal-fade-enter,
.modal-fade-leave-to {
  opacity: 0;
}

.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.5s ease;
}
</style>
