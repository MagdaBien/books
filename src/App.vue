<template>
  <div id="app">
    <!-- heading -->
    <header>
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
    books: [
      {
        title: 'The Catcher in the Rye',
        price: 20
      },
      {
        title: 'Of Mice and Men',
        price: 18
      }
    ]
  }),
  methods: {
    removeBook(index) {
      this.books.splice(index, 1)
    },
    addBook(book) {
      this.books.push({ ...book })
    }
  },
  computed: {
    booksPrice() {
      return this.books.reduce((total, book) => total + parseInt(book.price), 0)
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
