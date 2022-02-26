<template>
  <div class="container">
    <div class="card">
      <button
        :class="cardsCheck[id] ? 'cards disabled' : 'cards'"
        v-for="(items, id) in cards"
        :key="items.id"
        @click="
          isClicked ? `${clickCards1(items, id)}` : `${clickCards(items, id)}`,
            (isClicked = !isClicked)
        "
        :disabled="cardsCheck[id]"
      >
        <p v-if="cardsCheck[id]">{{ items }}</p>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: ["4", "2", "3", "4", "1", "2", "3", "1", "5", "6", "5", "6"],
      cardsCheck: [false, false, false, false, false, false, false, false],
      isClicked: false,
      isNumber: "",
      isNumber1: "",
    }
  },
  methods: {
    clickCards(items, id) {
      this.isNumber = items
      this.cardsCheck[id] = true
      console.log(this.cardsCheck)
      console.log("id", id)
    },
    clickCards1(items, id) {
      this.isNumber1 = items
      this.cardsCheck[id] = true
      let isNumberSaver = this.isNumber
      if (this.isNumber === this.isNumber1) {
        setTimeout(() => {
          console.log("id1", id)
          this.cards = this.cards.filter((f) => {
            return f !== isNumberSaver
          })
          this.cardsCheck = this.cardsCheck.filter((f) => {
            return f !== true
          })
        }, 800)
      } else {
        setTimeout(() => {
          this.cardsCheck = [
            false,
            false,
            false,
            false,
            false,
            false,
            false,
            false,
          ]
        }, 800)
      }
      /* this.isClicked = false */
      console.log(
        "this.isNumber",
        this.isNumber,
        "this.isNumber1",
        this.isNumber1
      )
    },
  },
}
</script>

<style></style>
