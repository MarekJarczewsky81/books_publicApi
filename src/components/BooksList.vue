<template>
  <div>
    <ul class="books-list">
      <book-item
        v-for="(book, index) in books"
        :key="index"
        :book="book"
        :index="index"
        @remove="handleRemove"
      />
    </ul>
    <p v-show="!books.length">No books...</p>
  </div>
</template>

<script>
import BookItem from './BookItem'

export default {
  name: 'BooksList',
  components: { BookItem },
  props: {
    books: {
      type: Array,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  methods: {
    handleRemove (index) {
      this.$emit('remove', index)
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
    border-bottom: .0625rem dashed rgba(0,0,0,.1);
  }

  &__btn {
    color: #fff;
    box-shadow: 0 10px 40px 0 rgba(76,104,239,.35), 0 0 20px 0 rgba(76,104,239,.05);
    border-radius: .3rem;
    border: none;
    font-family: inherit;
    text-transform: uppercase;
    font-weight: 700;
    min-width: 6rem;
    text-align: center;
    cursor: pointer;
    transition: .2s;
    background: #ea2027;
    color: #fff;
    padding: .5rem 1rem;
    font-size: .6rem;
    margin: 0 .5rem;

    &:hover {
      box-shadow: 0 20px 40px 0 rgba(76,104,239,.35);
    }
  }
}
</style>
