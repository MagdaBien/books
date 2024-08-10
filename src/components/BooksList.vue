<template>
  <div>
    <ul class="books-list">
      <BookItem
        v-for="(book, index) in books"
        :key="index"
        :book="book"
        :index="index"
        @remove="removeBook"
      />
    </ul>
    <p v-show="!books.length">No books...</p>
  </div>
</template>

<script>
import BookItem from './BookItem.vue'

export default {
  name: 'BooksList',
  props: {
    books: {
      type: Array,
      required: true
    }
  },
  methods: {
    removeBook(index) {
      this.$emit('remove', index)
    }
  },
  components: { BookItem }
}
</script>

<style lang="scss">
.books-list {
  font-size: 1rem;
  list-style-type: none;
  margin: 1rem 0;
  padding: 1rem;
  color: #637892;
  font-weight: 700;
}
</style>
