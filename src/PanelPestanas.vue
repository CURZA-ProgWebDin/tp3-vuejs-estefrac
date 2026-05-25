<template>
  <div>
    <div class="tabs">
      <BtnBase variant="primary" @click="tabActivo = TabTodos">Todos</BtnBase>
      <BtnBase variant="primary" @click="tabActivo = TabElectronica"
        >Electrónica</BtnBase
      >
      <BtnBase variant="primary" @click="tabActivo = TabPerifericos"
        >Periféricos</BtnBase
      >
    </div>
    <div class="comparacion">
      <div class="sinkeep">
        <h3>Sin KeepAlive</h3>
        <component :is="tabActivo" />
      </div>
      <div class="conkeep">
        <h3>Con KeepAlive</h3>
        <keep-alive>
          <component :is="tabActivo" />
        </keep-alive>
      </div>
    </div>
  </div>
</template>

<!--
Se utiliza KeepAlive cuando necesitamos conservar el estado de un componente. (Ejemplo: un formulario con datos ingresados, una lista con scroll, etc.)
No es necesario usarlo cuando necesitamos recargar datos o liberar memoria.
-->

<script setup>
import { shallowRef } from "vue";
import TabTodos from "./components/tabs/TabTodos.vue";
import TabElectronica from "./components/tabs/TabElectronica.vue";
import TabPerifericos from "./components/tabs/TabPerifericos.vue";
import BtnBase from "./components/BtnBase.vue";

const tabActivo = shallowRef(TabTodos);
</script>
<style scoped>
.tabs {
  display: flex;
  gap: 12px;
  justify-content: center;
  margin-bottom: 20px;
}
.comparacion {
  display: flex;
  gap: 20px;
}
.sinkeep,
.conkeep {
  flex: 1;
  min-width: 0;
}
h3 {
  text-align: center;
  color: #292e49;
  font-size: 1.1rem;
  margin-bottom: 12px;
}
</style>
