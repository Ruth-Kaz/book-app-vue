<template>
  <mainHeader />
  <main ref="start" class="container">
    <mainCatagories />
    <div ref="allBooks">
      <allBooks />
    </div>
  </main>
</template>

<script>
// Schritt 1: Komponente importieren
import mainHeader from '@/components/mainHeader.vue'
import mainCatagories from '@/components/mainCategories.vue'
import allBooks from '@/components/allBooks.vue'

export default {
  // Schritt 2: Komponente registrieren
  components: {
    mainHeader,
    mainCatagories,
    allBooks
  }
}
</script>

<style scoped></style>
