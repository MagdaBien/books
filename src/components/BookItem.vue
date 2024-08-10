<template>
  <li>
    {{ book.title }}, {{ book.price }}
    <button @click="removeBook">Remove</button>
  </li>
</template>

<script>
export default {
  name: 'BookItem',
  props: {
    book: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  methods: {
    removeBook() {
      this.$emit('remove', this.index)
    }
  }
}
</script>
