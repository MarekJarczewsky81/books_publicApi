<template>
  <div id="app" class="app">
    <!-- heading -->
    <header class="app__heading">
      <h1>Books<span>.app</span></h1>
    </header>

    <!-- books list -->
    <books-list :books="books" @remove="removeBook"/>

    <!-- no books message -->
    <books-length-msg :length="books.length" />
    <!-- add book form -->
    <book-form @add="addBook" />
    <!-- add book summary -->
    <books-summary :length="books.length" :books="books"/>
  </div>
</template>

<script>
import axios from 'axios'
import BooksList from './components/BooksList'
import BooksLengthMsg from './components/BooksLengthMsg'
import BookForm from './components/BookForm'
import BooksSummary from './components/BooksSummary'

export default {
  name: 'App',
  data: () => ({
    books: []
  }),
  components: { BooksList, BooksLengthMsg, BookForm, BooksSummary },
  created () {
    this.fetchBooks()
  },
  methods: {
    async fetchBooks () {
      try {
        const response = await axios.get('https://cors-anywhere.herokuapp.com/https://api.itbook.store/1.0/new')
        const book = response.data.books.slice(0, 3).map(book => ({
          title: book.title,
          price: book.price
        }))
        this.books = book
      } catch (error) {
        console.error(error)
      }
    },
    addBook (book) {
      this.books.push({ ...book })
    },
    removeBook (index) {
      this.books.splice(index, 1)
    }
  }
}
</script>

<style lang="scss">
.app {
  width: 100%;
  max-width: 1000px;
  padding: 2rem;
  margin: 0 auto;

  &__heading {
    font-size: 3rem;
    text-align: center;
    span {
      color: #5a58da;
    }
  }
}
</style>
