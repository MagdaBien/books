<template>
  <div>
    <p>Books amount: {{ booksAmount }}</p>
    <p>Books price: {{ booksPrice }}</p>
  </div>
</template>

<script>
export default {
  name: 'BooksSummary',
  props: {
    booksAmount: {
      type: Number,
      required: true
    },
    booksPrice: {
      type: Number,
      required: true
    }
  }
}
</script>
