<template>
  <ListaProductos :productos="filtrados" />
</template>
<script setup>
import { onMounted, onUnmounted, onActivated, onDeactivated } from "vue";
import { productos } from "../../data/productos.js";
import ListaProductos from "../ListaProductos.vue";

const filtrados = productos.filter(
  (producto) => producto.categoria === "Periféricos",
);

onMounted(() => {
  console.log("TabPerifericos montado");
});

onUnmounted(() => {
  console.log("TabPerifericos desmontado");
});

onActivated(() => {
  console.log("TabPerifericos activado");
});

onDeactivated(() => {
  console.log("TabPerifericos desactivado");
});
</script>
<style scoped></style>
