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
    <button class="btn" @click="generator">Генерация</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: ["4", "2", "3", "4", "1", "2", "3", "1", "5", "6", "5", "6"],
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
      generatorCounter:6,
    }
  },
  methods: {
    generator(){
      let arrGenerated = []
      for(let i = 0; i<this.generatorCounter; i++){
       let randomNumber = Math.floor(Math.random() * (10 - 1 + 1) + 1)
       console.log('i',i)
       if(arrGenerated.includes(randomNumber)){
         console.log('povtor','i',i)
         i--
       }
       else{
         arrGenerated.push(randomNumber,randomNumber)
         arrGenerated.join('')
         console.log(arrGenerated)
       }
      }
    },
    clickCards(items, id) {
      this.isNumber = items
      this.cardsCheck[id] = true
      console.log(this.cardsCheck)
      console.log("id", id)
    },
    clickCards1(items, id) {
      this.isNumber1 = items
      this.cardsCheck[id] = true
      if (this.isNumber === this.isNumber1) {
        setTimeout(() => {
          console.log("isNumber", this.isNumber)
          this.cards = this.cards.filter((f) => {
            return f !== this.isNumber
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
