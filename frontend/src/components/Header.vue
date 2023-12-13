<template>
  <header class="header">
    <div class="logo">Mon Logo</div>
    <!-- Autres éléments d'en-tête si nécessaire -->
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped>
.header {
  width: 100%;
  background-color: darkgreen;
  height: 4.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  color: white;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
}
</style>
