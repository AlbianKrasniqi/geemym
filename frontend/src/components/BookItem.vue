<template>
  <div class="card border-0 shadow position-relative">
    <img src="../../template/images/b1.jpg" alt="" class="card-img-top" />
    <div class="card-body">
      <div class="auth-box">
        <span
          style="background-color: #063547"
          class="py-1 px-3 text-white rounded-pill"
          >{{ book.author }}</span
        >
      </div>
      <h5 class="card-title mt-3 fw-semibold">{{ truncatedTextForTitles }}</h5>
      <p class="card-text">
        {{ truncatedText }}
      </p>
      <div class="d-flex justify-content-between align-items-center">
        <a href="#" class="card-link">Read more</a>
        <p
          style="background-color: #063547"
          class="py-1 px-2 text-white badge mb-0"
        >
          {{ book.uploadDate }}
        </p>
      </div>
    </div>
    <span
      :class="ratingBadgeClass"
      class="position-absolute top-0 start-100 translate-middle p-2 text-light rounded-circle border border-2 border-light"
      >{{ book.rating }}</span
    >
  </div>
</template>

<script>
export default {
  name: "BookItem",
  props: {
    book: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    ratingBadgeClass() {
      if (this.book.rating > 7) {
        return "bg-success";
      } else if (this.book.rating > 4) {
        return "bg-warning";
      } else {
        return "bg-danger";
      }
    },
    truncatedText() {
      if (this.book.description.length > 70) {
        return this.book.description.slice(0, 70) + "...";
      }

      return this.book.description;
    },
    truncatedTextForTitles() {
      if (this.book.name.length > 10) {
        return this.book.name.slice(0, 15) + "...";
      }
      return this.book.name;
    },
  },
};
</script>

<style scoped>
.card-text {
  min-height: 100px;
}
</style>
