<template>
  <article>
    <header>
      <slot name="header"></slot>
    </header>
    <div class="body">
      <slot
        name="body"
        :expandida="expandida"
        :toggleExpandir="toggleExpandir"
      ></slot>
    </div>
    <footer>
      <slot name="footer"><span>Sin acciones disponibles</span></slot>
    </footer>
  </article>
</template>

<script setup>
import { ref } from "vue";
const expandida = ref(false);
function toggleExpandir() {
  expandida.value = !expandida.value;
}
</script>

<style scoped>
article {
  display: flex;
  flex-direction: column;
  gap: 24px;
  width: 100%;
  min-width: 0;
  border: solid 1px #a8a8a8;
  border-radius: 10px;
  color: #536976;
  padding: 20px;
  background-image: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);

  header {
    flex-shrink: 0;
  }

  .body {
    flex: 1;
    overflow: visible;
    display: flex;
    flex-direction: column;
    gap: 8px;
    align-items: flex-start;
  }

  footer {
    flex: shrink 0;
    text-align: right;
  }
}
</style>
