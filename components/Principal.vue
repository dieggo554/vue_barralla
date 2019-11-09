<template>
    <html>

    <head>
      <title>Vue Transitions - Shuffle a Deck of Cards</title>
      <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>

      <link rel='stylesheet' href='https://cdnjs.cloudflare.com/ajax/libs/bulma/0.6.2/css/bulma.min.css'>
      <link rel='stylesheet' href='https://use.fontawesome.com/releases/v5.0.6/css/all.css'>
      <link rel="stylesheet" href="styles.css">
    </head>

    <body>
      <div id="app">
        <h1 class="title">
          <img class="vue-logo" src="https://vuejs.org/images/logo.png" />
          Card Shuffling
        </h1>
        <div class="deck">
          <div v-for="card in cards" :key="card.id"
          class="card"
          :class="suitColor[card.suit]">
            <span class="card__suit card__suit--top">{{ card.suit }}</span>
            <span class="card__number">{{ card.rank }}</span>
            <span class="card__suit card__suit--bottom">{{ card.suit }}</span>
          </div>
        </div>
      </div>

      <!-- <script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></script> -->
    </body>

  </html>
</template>

<script>
export default {
    data() {
        return {
                ranks: ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K'],
                suits: ['♥','♦','♠','♣'],
                cards: [],
                suitColor: {
                    '♠': 'black',
                    '♣': 'black',
                    '♦': 'red',
                    '♥': 'red',
                }
            }
    }, 
    created() {
        this.displayInitialDeck();
    },
    methods: {
        displayInitialDeck() {
            let id = 1;
            this.cards = [];

            for( let s = 0; s < this.suits.length; s++ ) {
                for( let r = 0; r < this.ranks.length; r++ ) {
                    let card = {
                        id: id,
                        rank: this.ranks[r],
                        suit: this.suits[s]
                    }
                    this.cards.push(card);
                    id++;
                }
            }
        },
    }
}
</script>

<style scoped>

</style>

