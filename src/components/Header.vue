<template lang="">
  <div class="nav">
    <img src="../assets/ic-logo.png" alt="pic" id="img" />
    <span v-if="this.listContact.length > 0">
      <button @click.stop.prevent="$emit('showModal')" class="new-phone">
        <img
          src="../assets/ic-plus.png"
          class="plus-button"
          alt="pic"
          id="img"
        />
        <div class="text-button">Criar contato</div>
      </button>
    </span>
    <span v-else><div class="div_none" /> </span>
    <div class="input-icons">
      <img
        src="../assets/ic-search.png"
        alt="pic"
        id="img"
        class="search-button"
      />
      <input
        v-model="message"
        class="busca_field"
        placeholder="Buscar..."
        type="text"
      />
    </div>
  </div>
</template>
<script>
export default {
  props: ["listContact", "showModal"],
  created: function () {
    // `this` aponta para a instância
    console.log("listContact", this.listContact);
  },
  methods: {
    logTeste: function () {
      let teste = this.listContact.push({ name: "teste" });
      this.listContact = teste;
      this.showModal;
    },
  },
};
</script>
<style scoped>
body {
  padding: 0px;
  margin: 0px;
}

.nav img {
  float: left;
  padding: 16px 0 0 0;
}

.nav button {
  width: 144px;
  height: 32px;
  margin: 16px 24px 0 60px;
  padding: 8px 22px 8px 16px;
  border-radius: 20px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #dbff90;
  border-color: transparent;
  float: left;
}

.text-button {
  width: 82px;
  height: 16px;
  margin: 0 0 0 24px;
  font-family: Roboto;
  font-size: 14px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #fa7268;
}

.input-icons img {
  position: absolute;
}

.new-phone {
  cursor: pointer;
}

.search-button {
  height: 16px;
  width: 16px;
  right: 24px;
  margin-right: 8px;
  padding: 24px 0 0 0 !important;
}

.input-icons {
  width: 100%;
  margin-bottom: 10px;
}

.icon {
  padding: 10px;
  min-width: 40px;
}

.input-field {
  width: 100%;
  padding: 10px;
  text-align: center;
}

.div_none {
  width: 144px;
  height: 32px;
  margin: 16px 8px 0 60px;
  padding: 8px 0px 8px 16px;
  border-radius: 20px;
  float: left;
}

.plus-button {
  width: 16px;
  height: 16px;
  padding: 0 !important;
}

.busca_field {
  width: 1436px;
  max-height: 32px;
  margin: 16px 0 0 24px;
  padding: 7px 8px 6px;
  border-radius: 4px;
  background-color: #e4e7f4;
  border-color: transparent;
}

.nav {
  background-color: #f8f9fd;
  overflow: hidden;
}
</style>
