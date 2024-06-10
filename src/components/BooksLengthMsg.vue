<template>
  <div>
    <p v-show="length">Actually we'have:</p>
    <p v-if="length > 5">{{ length }} books</p>
    <p v-else-if="length > 1 && length <= 5">Not too many of them...</p>
    <p v-if="length === 1">One single book!</p>
    <p v-if="length < 1">Go get some books!</p>
  </div>
</template>

<script>
export default {
  name: 'BooksLengthMsg',
  props: {
    length: {
      type: Number,
      required: true
    }
  }
}
</script>
