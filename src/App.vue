<template>
  <div class="container">
    <div class="card">
      <button
        :class="cardsCheck[id] ? 'cards disabled' : 'cards'"
        v-for="(items, id) in cards"
        :key="items.id"
        @click="
          isClicked ? `${clickCards1(items, id)}` : `${clickCards(items, id)}`
        "
        :disabled="cardsCheck[id]"
      >
        <p>{{ items }}</p>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: ["4", "2", "3", "4", "1", "2", "3", "1", "1", "2", "3", "1"],
      cardsCheck: [
        false,
        false,
        false,
        false,
        false,
        false,
        false,
        false,
        false,
        false,
        false,
        false,
      ],
      isClicked: false,
      isNumber: "",
      isNumber1: "",
      idSaver: "",
      idSaver1: "",
    }
  },
  methods: {
    clickCards(items, id) {
      this.isNumber = items
      this.cardsCheck[id] = true
      console.log(this.cardsCheck)
      this.isClicked = true
      this.idSaver = id
      console.log("id", id)
    },
    clickCards1(items, id) {
      this.isNumber1 = items
      this.cardsCheck[id] = true
      let isNumberSaver = this.isNumber
      this.idSaver1 = id
      if (this.isNumber === this.isNumber1) {
        console.log("id1", id)
        this.cardsCheck.splice(id, 1)
        this.cardsCheck.splice(id, 1)
        this.cards = this.cards.filter((f) => {
          return f !== isNumberSaver
        })
        this.isClicked = false
      }
      /* this.isClicked = false */
      console.log(id)
    },
  },
}
</script>

<style></style>
