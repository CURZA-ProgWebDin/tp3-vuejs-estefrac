<script setup>
import TarjetaProducto from "./components/TarjetaProducto.vue";
import BtnBase from "./components/BtnBase.vue";
import ListaProductos from "./components/ListaProductos.vue";
import PanelPestanas from "./PanelPestanas.vue";
import { productos } from "./data/productos.js";
</script>

<template>
  <h1 style="color: #536976; font-size: 40px; font-weight: 900">
    <span class="titulo-gradiente">TP3</span> - Ciclo de vida, componentes
    dinámicos y slots
  </h1>
  <div class="catalogo">
    <div class="contenido">
      <div class="parte1">
        <h2 style="color: #536976; font-size: 30px">Parte 1 — Slots</h2>

        <div class="scroll-lista">
          <TarjetaProducto>
            <template #header>
              <div class="header-contenido">
                <h2>{{ productos[0].nombre }}</h2>
                <span>{{ productos[0].categoria }}</span>
              </div>
            </template>
            <template #body="{ expandida, toggleExpandir }">
              <p>
                <span style="font-weight: 700">Precio:</span> ${{
                  productos[0].precio.toLocaleString()
                }}
              </p>
              <p>
                <span style="font-weight: 700">Stock:</span>
                {{ productos[0].stock }} unidades
              </p>
              <p v-if="expandida">
                {{ productos[0].descripcion }}
              </p>

              <BtnBase @click="toggleExpandir">
                {{ expandida ? "Ver menos ↑" : "Ver más ↓" }}
              </BtnBase>
            </template>
            <template #footer
              ><BtnBase variant="primary">Comprar</BtnBase></template
            >
          </TarjetaProducto>

          <TarjetaProducto>
            <template #header>
              <div class="header-contenido">
                <h2>{{ productos[1].nombre }}</h2>
                <span>{{ productos[1].categoria }}</span>
              </div>
            </template>
            <template #body="{ expandida, toggleExpandir }">
              <p>
                <span style="font-weight: 700">Precio:</span> ${{
                  productos[1].precio.toLocaleString()
                }}
              </p>
              <p>
                <span style="font-weight: 700">Stock:</span>
                {{ productos[1].stock }} unidades
              </p>
              <p v-if="expandida">
                {{ productos[1].descripcion }}
              </p>

              <BtnBase @click="toggleExpandir">
                {{ expandida ? "Ver menos ↑" : "Ver más ↓" }}
              </BtnBase>
            </template>
          </TarjetaProducto>

          <TarjetaProducto>
            <template #header>
              <div class="header-contenido">
                <h2>{{ productos[2].nombre }}</h2>
                <span>{{ productos[2].categoria }}</span>
              </div>
            </template>
            <template #body="{ expandida, toggleExpandir }">
              <p>
                <span style="font-weight: 700">Precio:</span> ${{
                  productos[2].precio.toLocaleString()
                }}
              </p>
              <p>
                <span style="font-weight: 700">Stock:</span>
                {{ productos[2].stock }} unidades
              </p>
              <p v-if="expandida">
                {{ productos[2].descripcion }}
              </p>

              <BtnBase @click="toggleExpandir">
                {{ expandida ? "Ver menos ↑" : "Ver más ↓" }}
              </BtnBase>
            </template>
            <template #footer
              ><div
                style="
                  display: flex;
                  justify-content: space-between;
                  width: 100%;
                "
              >
                <BtnBase variant="secondary">Ver reseñas</BtnBase
                ><BtnBase variant="primary">Comprar</BtnBase>
              </div></template
            >
          </TarjetaProducto>
        </div>
      </div>
      <div class="parte2">
        <h2 style="color: #536976; font-size: 30px">Parte 2 — Ciclo de vida</h2>
        <ListaProductos :productos="productos" />
      </div>
    </div>

    <h2 style="color: #536976; font-size: 30px">
      Parte 3 — Componentes dinámicos
    </h2>
    <PanelPestanas />
  </div>
</template>

<style scoped>
.catalogo {
  display: flex;
  flex-direction: column;
  gap: 24px;
  padding: 32px;
  align-items: center;
}

.header-contenido {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.titulo-gradiente {
  background: -webkit-linear-gradient(315deg, #42d392 25%, #647eff);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}

.contenido {
  display: flex;
  gap: 24px;
}

.parte1 {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.parte2 {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  gap: 16px;
  overflow-x: hidden;
}

.scroll-lista {
  width: 600px;
  min-width: 600px;
  max-width: 600px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 16px;
}
</style>
