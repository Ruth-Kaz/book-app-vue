<template>
  <section ref="allBooks" id="all-books" class="section">
    <h2>All Books</h2>
    <div class="book-info section-content">
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
        </div>
      </div>
    </div>

    <div id="pagination" class="pagination">
      <button @click="prevPage" v-show="currentPage > 1" class="pagination-button">Previous</button>
      <span>Page {{ currentPage }} of {{ totalPages }}</span>
      <button @click="nextPage" :disabled="currentPage === totalPages" class="pagination-button">
        Next
      </button>
    </div>
    <span>Page {{ currentPage }} of {{ totalPages }}</span>
  </section>
</template>

<script>
export default {
  data() {
    return {
      books: [], // Array to store fetched books
      error: '', // Error message if any
      searchQuery: '', // Search query
      currentPage: 1, // Current page number
      booksPerPage: 6 // Number of books to display per page
    }
  },

  computed: {
    totalPages() {
      return Math.ceil(this.books.length / this.booksPerPage)
    },

    // Calculate portion of books for current page
    paginatedData() {
      const startIndex = (this.currentPage - 1) * this.booksPerPage
      const endIndex = startIndex + this.booksPerPage
      return this.books.slice(startIndex, endIndex)
    }
  },

  mounted() {
    this.typeWriter()
  },

  methods: {
    // Go to the previous page
    prevPage() {
      if (this.currentPage > 1) {
        this.currentPage--
      }
    },
    // Go to the next page
    nextPage() {
      if (this.currentPage < this.totalPages) {
        this.currentPage++
      }
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

<style scoped>
.book {
  background-color: var(--glass-background);
  text-decoration: none;
  padding: 0 1rem;
}

.book-content {
  display: grid;
  grid-template-columns: 1fr;
  grid-auto-rows: 3rem 2.2rem 3rem;
  gap: 1rem;
  justify-content: flex-start;
  flex-grow: 1;
}

.book-content h3,
p {
  color: var(--color);
  margin: 0;
}

.book-info {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 2.5rem;
  flex-direction: column;
  align-items: flex-start;
  justify-content: space-between;
}

#book-info img {
  max-width: 200px;
}

.pagination {
  display: flex;
  width: 23rem;
  height: 3rem;
  margin: auto;
  background-color: var(--glass-background);
  border-radius: 0.4rem;
  place-items: center;
  justify-content: center;
}

.pagination-button {
  color: var(--color);
  float: none;
  width: 5rem;
  padding: 0;
  border: none;
  text-decoration: none;
  background-color: #ffffff00;
}

.pagination-button:hover:not(.active) {
  background-color: var(--dark-blue);
  color: var(--color);
  border-radius: 5px;
}
</style>
