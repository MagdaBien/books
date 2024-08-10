<template>
  <div>
    <ul>
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
