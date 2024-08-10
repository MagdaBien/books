<template>
  <div id="app">
    <!-- heading -->
    <header class="app__heading">
      <h1>Books<span>.app</span></h1>
    </header>

    <!-- books list -->
    <books-list :books="books" @remove="removeBook" />

    <!-- books message -->
    <books-length-msg :booksAmount="books.length" />

    <!-- add book form -->
    <book-form @add="addBook" />

    <books-summary :booksAmount="books.length" :booksPrice="booksPrice" />
  </div>
</template>

<script>
import BooksList from './components/BooksList'
import BooksLengthMsg from './components/BooksLengthMsg'
import BookForm from './components/BookForm'
import BooksSummary from './components/BooksSummary'

export default {
  name: 'App',
  data: () => ({
    books: []
  }),
  methods: {
    removeBook(index) {
      this.books.splice(index, 1)
    },
    addBook(book) {
      this.books.push({ ...book })
    },
    async fetchBooks() {
      try {
        const response = await fetch('https://api.itbook.store/1.0/new')
        const data = await response.json()
        data.books.slice(0, 3).map((book) =>
          this.books.push({
            title: book.title,
            price: parseFloat(book.price.match(/[\d.]+/)).toFixed(2)
          })
        )
      } catch (error) {
        console.error('Error fetching books:', error)
      }
    }
  },
  created() {
    this.fetchBooks()
  },
  computed: {
    booksPrice() {
      return this.books
        .reduce((total, book) => total + parseFloat(book.price), 0)
        .toFixed(2)
    }
  },
  components: {
    BooksList,
    BooksLengthMsg,
    BookForm,
    BooksSummary
  }
}
</script>

<style lang="scss">
.app {
  width: 100%;
  max-width: 1000px;
  padding: 2rem;
  margin: 0 auto;

  &__heading {
    font-size: 3rem;
    text-align: center;
    span {
      color: #5a58da;
    }
  }
}
</style>
