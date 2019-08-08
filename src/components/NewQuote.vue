<template>
  <div class="row" style="margin-bottom: 15px">
    <form>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-offset">
        <label>Quote</label>
        <textarea class="form-control" rows="3" v-model="text"></textarea>
      </div>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-offset">
        <button class="btn btn-primary" @click.prevent="createNew">Add Quote</button>
      </div>
    </form>
  </div>
</template>


<script>
import uuid from "uuid/v4";

export default {
  props: ["quotes", "maxQuotes"],
  data() {
    return {
      text: ""
    };
  },
  methods: {
    createNew() {
      if (this.quotes.length >= this.maxQuotes) {
        alert("Maximum quotes reachead!");
        return;
      }

      if (this.text.length === 0) {
        alert("Enter a text in the text area");
        return;
      }

      const quote = {
        id: uuid(),
        text: this.text
      };
      this.$emit("quoteAdded", quote);
      this.text = "";
    }
  }
};
</script>

<style >
</style>