<template>
  <button :class="['btn-base', variant]" @click="$emit('click')">
    <slot />
  </button>
</template>

<script setup>
defineProps({
  variant: {
    type: String,
    default: "link",
    validator: (v) => ["link", "primary", "secondary"].includes(v),
  },
});
defineEmits(["click"]);
</script>

<style scoped>
.btn-base {
  font: inherit;
  cursor: pointer;
  border: none;
  padding: 5px 12px;
  border-radius: 6px;
}
/* Ver más */
.link {
  background: none;
  border: 1px solid;
  color: inherit;
  font-size: 0.85rem;
}
.link:hover {
  color: #004499;
}
/* Comprar */
.primary {
  background: #292e49;
  color: white;
  padding: 8px 24px;
}
/* Ver reseñas */
.secondary {
  background: none;
  border: 1px solid #292e49;
  color: #292e49;
  padding: 8px 24px;
}
</style>
