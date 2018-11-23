<template>
  <div id="app">
    <paginacao
      :total-elements="TOTAL_ELEMENTS"
      :items-per-page="ITEMS_PER_PAGE"
      :current-page="currentPage"
      @change-page="changePage"
    />
  </div>
</template>

<script>
import Paginacao from './components/Pagination';

const TOTAL_ELEMENTS = 103; // vem junto com a lista de itens
const ITEMS_PER_PAGE = 20; // geralmente uma configuracao pre determinada

export default {
  name: 'app',
  components: {
    Paginacao,
  },
  data() {
    return {
      TOTAL_ELEMENTS,
      ITEMS_PER_PAGE,
      currentPage: 1,
    }
  },
  methods: {
    changePage(page) {
      console.log(page);
      this.currentPage = page;
    }
  },
}
</script>
