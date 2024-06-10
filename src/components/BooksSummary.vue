<template>
  <div>
    <p>Books amount: {{ length }}</p>
    <p>Books price: {{ totalPrice }}</p>
  </div>
</template>

<script>
import { computed } from 'vue'

export default {
  name: 'BooksSummary',
  props: {
    length: {
      type: Number,
      required: true
    },
    books: {
      type: Array,
      required: true
    }
  },
  computed: {
    totalPrice () {
      let sum = 0
      for (const book of this.books) {
        sum += computed(() => parseInt(book.price)).value
      }
      return sum
    }
  }
}
</script>
