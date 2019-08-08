<template>
  <div class="row">
    <Quote
      :key="quote.id"
      v-for="(quote,index) in quotes"
      @click.native="deleteQuote(index)"
    >{{quote.text}}</Quote>
  </div>
</template>

<script>
import Quote from "./Quote.vue";
export default {
  props: ["quotes"],
  components: {
    Quote
  },
  methods: {
    deleteQuote(index) {
      this.$emit("quoteDeleted", index);
    }
  }
};
</script>

<style scoped>
</style>