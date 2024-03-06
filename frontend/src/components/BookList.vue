<template>
  <div class="row">
    <div class="col-sm-6 col-md-4 cold-xl-3 mb-4" v-for="book in books">
      <BookItem :book="book" :key="book.id" />
    </div>
  </div>
</template>

<script>
import BookItem from "@/components/BookItem.vue";
export default {
  name: "BookList",
  components: {
    BookItem,
  },
  props: {
    books: {
      type: Array,
      default: () => {
        [];
      },
    },
  },
};
</script>

<style lang="scss" scoped></style>
