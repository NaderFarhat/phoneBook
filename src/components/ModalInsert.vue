<script>
export default {
  name: "ModalInsert",
  props: ["listContact"],
  data() {
    return {
      id: "",
      name: "",
      email: "",
      phone: "",
      last: false,
    };
  },
  computed: {
    isDisabled: function () {
      if (
        this.name.length > 0 &&
        this.email.length > 0 &&
        this.phone.length > 0
      ) {
        return false;
      } else {
        return true;
      }
    },
  },
  methods: {
    close() {
      this.$emit("close");
    },
    sendData() {
      let teste = this.listContact.push({
        id: this.listContact.length + 1,
        name: this.name,
        email: this.email,
        phone: this.phone,
        last: true,
      });
      this.listContact = teste;
      this.$emit("close");
    },
  },
};
</script>

<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div
        class="modalInsert"
        role="dialog"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header class="modal-header" id="modalTitle">
          <div name="header" class="header">Criar novo contato</div>
        </header>

        <section class="modal-body" id="modalDescription">
          <div>
            <div class="label">Nome</div>
            <div class="d-flex">
              <input v-model="name" class="text_field" />
            </div>
          </div>
          <div>
            <div class="label label-email">E-mail</div>
            <div class="d-flex">
              <input v-model="email" class="text_field" />
            </div>
          </div>
          <div>
            <div class="label">Telefone</div>
            <div class="d-flex">
              <input
                v-model="phone"
                class="text_field-phone"
                v-mask="'+55 (##) #########'"
              />
            </div>
          </div>
        </section>

        <footer class="modal-footer">
          <button
            type="button"
            class="btn-close"
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
            :disabled="isDisabled"
          >
            Salvar
          </button>
        </footer>
      </div>
    </div>
  </transition>
</template>

<style>
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

.modalInsert {
  width: 432px;
  height: 342px;
  padding: 16px 0;
  border-radius: 16px;
  box-shadow: 0 16px 10px 0 rgba(0, 0, 0, 0.16);
  background-color: #ffffff;
}

.d-flex {
  display: flex;
}

.modal-header,
.modal-footer {
  padding: 9px 15px;
  display: flex;
}

.modal-footer {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
}

.modal-header {
  position: relative;
  border-bottom: 2px solid #eeeeee;
  color: #2a2d3b !important;
  justify-content: space-between;
}

.label {
  text-align: initial;
  margin-top: 20px;
}

.modal-footer {
  border-top: 2px solid #eeeeee;
  display: flex;
  flex-direction: row;
}

.modal-body {
  position: relative;
  padding: 0px 24px 22px 24px !important;
}

.text_field {
  width: 384px;
  height: 32px;
  margin: 4px 0px 0px;
  border-radius: 4px;
  border: solid 1px #c0c3d2;
  background-color: var(--white-two);
}

.label-email {
  margin-top: 16px !important;
}

.text_field-phone {
  width: 128px;
  height: 32px;
  margin: 4px 120px 0px 0px;
  border-radius: 4px;
  border: solid 1px #c0c3d2;
  background-color: var(--white-two);
}

.btn-close {
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
  margin: 0px 16px 0 60px !important;
  color: #fa7268 !important;
  cursor: pointer;
}

.btn-green {
  color: white;
  background: #4aae9b;
  border: 1px solid #4aae9b;
  border-radius: 2px;
}

button:disabled,
button[disabled] {
  width: 72px;
  height: 32px;
  padding: 8px 16px;
  opacity: 0.32;
  border-radius: 16px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #fa7268;
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
