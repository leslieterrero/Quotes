<template>
  <div class= "container">
   <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
   <app-many-quotes :quotes="quotes" @quoteDeleted="eraseQuote"> </app-many-quotes>
   <app-new-quote @quoteAdded="addNewQ"> </app-new-quote>

   <div class="row">
      <div class="col-sm-12 text-center">
      <div class="alert alert-info">Info: Click on a quote to delete it (:</div>
      </div>


    </div>
  </div>
</template>

<script>

import ManyQuotes from './components/ManyQuotes.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/Header.vue';


export default {

  data: function () {
    return {

      quotes: [
      
      'Good things take time'

      ],

      maxQuotes: 10
    }
  },

  methods: {
   addNewQ(quote) {
                if (this.quotes.length >= this.maxQuotes) {
                    return alert('Please delete some Quotes first!');
                }
                this.quotes.push(quote);
            },


    eraseQuote(index){
      this.quotes.splice(index, 1);
    }
  },

 components: {


   appManyQuotes: ManyQuotes,
   appNewQuote: NewQuote,
   appHeader: Header
  
 }

}
</script>

<style>


</style>
