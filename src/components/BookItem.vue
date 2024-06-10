<template>
  <li
    class="books-list__item"
    :class="{'books-list__item--promotion': book.price < 20}">
    {{ book.title }}, {{ book.price }}
    <!-- <button @click="removeBook(index)">Remove</button> -->
    <button
      class="books-list__btn"
      @click="$emit('remove', index)"
      v-text="'Remove book'" />
    <!--funkcja $emit: przycisk emituje do rodzica event remove, przy okazji przekazując też informacje o indeksie książki do usunięcia -->
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
  }
}
</script>

<style lang="scss">
.books-list__item {
    padding: 1rem 0;
    border-bottom: .0625rem dashed rgba(0,0,0,.1);

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

  &--promotion {
    font-size: 1.5rem;
    text-decoration: underline;
  }
}
</style>
