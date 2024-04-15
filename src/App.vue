<template>
  <div>
    <!-- <p>{{ JSON.stringify(cards) }}</p> -->

    <h1>
      Magic Card Generator:
    </h1>
    <ul>
      <li v-for="card in cards">
        <h3>{{ card.name }}</h3>
        <img :src="card.img" alt="">
      </li>
    </ul>
    <appCards :pippo="'ciao'" :pluto="5" />
  </div>
</template>

<script>
import axios from 'axios';
import appCards from './components/appCards.vue'

export default {
  data() {


    return {
      components: {
        appCards,
      },
      cards: []
    }
  },
  methods: {
    getRandomCard() {
      for (let i = 0; i < 5; i++) {
        axios.get('https://api.scryfall.com/cards/random').then((res) => {
          console.log(res)
          const data = res.data;

          const name = data.name;
          const img = data.image_uris.normal;


          this.cards.push({
            name: name,
            img: img,
          }

          )
        })
      }

    }
  },

  mounted() {
    this.getRandomCard()

  }

}
</script>

<style lang="scss" scoped></style>