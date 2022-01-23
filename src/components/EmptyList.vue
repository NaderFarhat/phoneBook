<template lang="">
  <div class="container_empty">
    <img src="../assets/ic-book.png" alt="pic" id="img" />
    <div class="text-empty">Nenhum contato foi criado ainda.</div>
    <button @click.stop.prevent="$emit('showModal')" class="new-phone">
      <img src="../assets/ic-plus.png" class="plus-button" alt="pic" id="img" />
      <div class="text-button">Criar contato</div>
    </button>
  </div>
</template>
<script>
export default {
  props: ["listContact", "showModal"],
};
</script>
<style>
button {
  width: 144px;
  height: 32px;
  margin: 16px 24px 0 24px;
  padding: 8px 22px 8px 16px;
  border-radius: 20px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #dbff90;
  border-color: transparent;
  float: center;
}

.text-button {
  width: 82px;
  height: 16px;
  margin: 0 0 0 24px;
  font-family: Roboto;
  font-size: 14px;
  font-weight: 600;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #fa7268;
}

.text-empty {
  margin: 24px 0;
  font-family: Roboto;
  font-size: 16px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-align: center;
  color: #2a2d3b;
}

.new-phone {
  width: 144px;
  height: 40px;
  margin: 0px 47px 0;
  padding: 12px 22px 12px 16px;
  border-radius: 20px;
  box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.16),
    0 0 0 0.5px rgba(0, 0, 0, 0.08), inset 0 0 0 0.5px rgba(0, 0, 0, 0.08),
    0 2px 4px 0.5px rgba(0, 0, 0, 0.16);
  background-color: #dbff90;
  cursor: pointer;
}

.plus-button {
  width: 16px;
  height: 16px;
  padding: 0 !important;
  float: left;
}

.container_empty {
  margin-top: 96px;
}

img {
  float: center;
  padding: 16px 16px;
}
</style>
