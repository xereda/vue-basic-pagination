<template>
  <div>
    <button 
      v-for="page in totalPages" 
      :key="page"
      @click="onClick(page)"
      :disabled="isDisabled(page)"
    >
      {{ page }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'Pagination',  
  props: {
    totalElements: Number,
    itemsPerPage: Number,
    currentPage: Number,
  },
  computed: {
    totalPagesWithoutFix() {
      return (this.totalElements / this.itemsPerPage);
    },
    hasBreakedItems() {
      return (this.totalPagesFixed * this.itemsPerPage) < this.totalElements;
    },
    totalPagesFixed() {
      return Number(this.totalPagesWithoutFix.toFixed());
    },
    totalPages() {
      return this.hasBreakedItems ? 
        this.totalPagesFixed + 1 : 
        this.totalPagesFixed;
    }
  },
  methods: {
    onClick(page) {
      this.$emit('change-page', page);
    },
    isDisabled(page) {
      return this.currentPage === page;
    }
  }
}
</script>
