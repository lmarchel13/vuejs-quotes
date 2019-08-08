<template>
  <div class="container">
    <Header :quotesCount="quotes.length" :maxQuotes="maxQuotes"></Header>
    <NewQuote @quoteAdded="newQuote" :quotes="quotes" :maxQuotes="maxQuotes"></NewQuote>
    <QuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></QuoteGrid>
    <div class="row">
      <div class="col-sm-12 text-center" style="margin-top: 10px">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";

export default {
  data() {
    return {
      quotes: [],
      maxQuotes: 10
    };
  },
  components: {
    Header,
    QuoteGrid,
    NewQuote
  },
  methods: {
    newQuote(quote) {
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
</style>
