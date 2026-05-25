<template>
  <ListaProductos :productos="filtrados" />
</template>
<script setup>
import { onMounted, onUnmounted, onActivated, onDeactivated } from "vue";
import { productos } from "../../data/productos.js";
import ListaProductos from "../ListaProductos.vue";

const filtrados = productos.filter(
  (producto) => producto.categoria === "Electrónica",
);

onMounted(() => {
  console.log("TabElectronica montado");
});

onUnmounted(() => {
  console.log("TabElectronica desmontado");
});

onActivated(() => {
  console.log("TabElectronica activado");
});

onDeactivated(() => {
  console.log("TabElectronica desactivado");
});
</script>
<style scoped></style>
