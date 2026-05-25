<template>
  <div ref="box" class="lista">
    <p v-if="cargando" style="font-size: 24px; color: #536976">Cargando.....</p>
    <TarjetaProducto v-else v-for="producto in productos" :key="producto.id">
      <template #header>
        <div class="header-contenido">
          <h2>{{ producto.nombre }}</h2>
          <span>{{ producto.categoria }}</span>
        </div>
      </template>
      <template #body="{ expandida, toggleExpandir }">
        <p>
          <span style="font-weight: 700">Precio:</span> ${{
            producto.precio.toLocaleString()
          }}
        </p>
        <p>
          <span style="font-weight: 700">Stock:</span>
          {{ producto.stock }} unidades
        </p>
        <p v-if="expandida">
          {{ producto.descripcion }}
        </p>

        <BtnBase @click="toggleExpandir">
          {{ expandida ? "Ver menos ↑" : "Ver más ↓" }}
        </BtnBase>
      </template>
      <template #footer><BtnBase variant="primary">Comprar</BtnBase></template>
    </TarjetaProducto>
  </div>
</template>
<script setup>
import { ref, onMounted, onUpdated, onBeforeUnmount } from "vue";
import { useTemplateRef } from "vue";
import TarjetaProducto from "./TarjetaProducto.vue";
import BtnBase from "./BtnBase.vue";

const props = defineProps({ productos: { type: Array, required: true } });
const box = useTemplateRef("box");
const cargando = ref(true);
let timer;

function esperar(ms) {
  return new Promise((resolve) => setTimeout(resolve, ms));
}

async function cargarProductos() {
  cargando.value = true;
  await esperar(800);
  cargando.value = false;
}

onMounted(() => {
  cargarProductos();
  timer = setInterval(cargarProductos, 30000);
});

onUpdated(() => {
  if (box.value) {
    box.value.scrollTop = box.value.scrollHeight;
  }
});

onBeforeUnmount(() => {
  clearInterval(timer);
  console.log("ListaProductos desmontado — polling detenido");
});
</script>
<style>
.header-contenido {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.lista {
  width: 600px;
  min-width: 600px;
  max-width: 600px;
  height: 800px;
  max-height: 800px;
  overflow-x: hidden;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 16px;
}
</style>
