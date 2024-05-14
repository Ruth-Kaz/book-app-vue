<template>
  <div id="book-details" class="section-content glass-effect">
    <button>x</button>
    <div
      v-for="book in paginatedData"
      :key="book.id"
      :href="`./details/index.html?id=${book.id}`"
      class="book glass-effect"
    >
      <img :src="book.cover" :alt="book.title" />
      <div class="book-content">
        <h3>{{ book.title }}</h3>
        <p>{{ book.author }}</p>
        <p>ISBN: {{ book.isbn }}</p>
        <p>{{ book.abstract }}</p>
        <button>buy</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      book: null,
      error: ''
    }
  },

  computed: {
    // Calculate portion of books for current page
    paginatedData() {
      const startIndex = (this.currentPage - 1) * this.booksPerPage
      const endIndex = startIndex + this.booksPerPage
      return this.books.slice(startIndex, endIndex)
    }
  },

  async created() {
    try {
      const response = await fetch('http://localhost:4730/books')
      if (!response.ok) {
        throw new Error('Failed to fetch data')
      }
      const data = await response.json()
      this.books = data
    } catch (error) {
      console.error('Error fetching data:', error)
      this.error = 'Something went wrong! :('
    }
  }
}
</script>
