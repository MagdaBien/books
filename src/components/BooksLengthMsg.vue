<template>
  <div>
    <p v-if="booksAmount === 1">One single book!</p>
    <p v-else-if="booksAmount > 1 && booksAmount <= 5">
      Not too many of them ...
    </p>
    <p v-else-if="booksAmount > 5">{{ booksAmount }} books</p>
    <p v-else>Go get some books!</p>
  </div>
</template>

<script>
export default {
  name: 'BooksLengthMsg',
  props: {
    booksAmount: {
      type: Number,
      required: true
    }
  }
}
</script>
