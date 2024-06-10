<template>
  <div>
    <form
      class="form"
      @submit.prevent="$emit('add', form), handleSubmit" >
      <label>
        Title:
        <input
          class="form__input"
          v-model="form.title"
          type="text"
          name="title">
      </label>
      <label>
        Price:
        <input
          class="form__input"
          v-model="form.price"
          type="number"
          name="price" >
      </label>
      <button
        class="form__btn"
        v-text="'Add book'" />
    </form>
  </div>
</template>

<script>
export default {
  name: 'BookForm',
  data: () => ({
    form: {
      title: '',
      price: 0
    }
  }),
  methods: {
    handleSubmit () {
      this.$emit('add', this.form)
    // here is your code for emptying the form
    }
  }
}
</script>

<style lang="scss">
.form {
  border-radius: 2rem;
  margin: 4rem 1rem;
  box-shadow: 0 20px 40px 0 rgba(107,154,212,.1);
  padding: 2rem;
  background: #fff;
  position: relative;
  overflow: hidden;
  font-size: 1rem;
  color: #637892;

  &__input {
    background: none;
    border: none;
    outline: none;
    padding: .7rem .7rem .7rem .7rem;
    color: #000;
    font-weight: lighter;
    font-family: inherit;
    border-bottom: 1px solid #5a58da;
    margin: .5rem;
    opacity: .8;
    width: 100%;
    max-width: 20rem;
    transition: .2s;
    font-size: 1rem;
  }

  &__btn {
    padding: 1rem 1.5rem;
    border: none;
    box-shadow: 0 10px 40px 0 rgba(76,104,239,.35), 0 0 20px 0 rgba(76,104,239,.05);
    font-family: inherit;
    text-transform: uppercase;
    font-weight: 700;
    min-width: 6rem;
    text-align: center;
    margin: 2rem auto;
    display: table;
    cursor: pointer;
    transition: .2s;
    background: #f2f8ff;
    color: #5a58da;
    border: 2px solid #5a58da;
    border-radius: 0.5rem;
  }
}
</style>
