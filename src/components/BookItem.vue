<template>
  <li
    class="books-list__item"
    :class="book.price < 20 && 'books-list__item--promotion'"
  >
    {{ book.title }}, {{ book.price }}
    <button @click="removeBook" class="books-list__btn">Remove</button>
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

<style lang="scss">
.books-list {
  font-size: 1rem;
  list-style-type: none;
  margin: 1rem 0;
  padding: 1rem;
  color: #637892;
  font-weight: 700;

  &__item {
    padding: 1rem 0;
    border-bottom: 0.0625rem dashed rgba(0, 0, 0, 0.1);
  }
  &__item--promotion {
    font-size: 1.5rem;
    text-decoration: underline;
  }

  &__btn {
    color: #fff;
    box-shadow: 0 10px 40px 0 rgba(76, 104, 239, 0.35),
      0 0 20px 0 rgba(76, 104, 239, 0.05);
    border-radius: 0.3rem;
    border: none;
    font-family: inherit;
    text-transform: uppercase;
    font-weight: 700;
    min-width: 6rem;
    text-align: center;
    cursor: pointer;
    transition: 0.2s;
    background: #ea2027;
    color: #fff;
    padding: 0.5rem 1rem;
    font-size: 0.6rem;
    margin: 0 0.5rem;

    &:hover {
      box-shadow: 0 20px 40px 0 rgba(76, 104, 239, 0.35);
    }
  }
}
</style>
