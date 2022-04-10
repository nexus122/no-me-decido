<template>
  <div class="card" :number="number">
    <textarea v-model="text2" :placeholder="placeholderFunction(number-1)" @keyup="PasarTextoAlPadre(text2, number)">text</textarea>
  </div>
</template>

<style scoped>
.card {
  background: transparent;
  width: 250px;
  height: 75px;
  margin-left: 5px;
  margin-top: 5px;
  border: 3px solid white;
  border-radius: 1em;
  padding: 1em;
  box-sizing: border-box;
}

textarea {
  background-color: transparent;
  font-family: "Bebas Neue", cursive;
  font-size: 1.5em;
  outline: none;
  resize: none;
  cursor: pointer;
  width: 100%;
  height: 100%;
  padding: 0px;
  margin: 0px;
  border: 0px;
  color: white;
}
</style>

<script>
export default {
  name: "Card",  
  data() {
    return {
      text2: this.text,
      placeholder: [
        "Esto",
        "O Esto",
        "O Esta otra cosa",
        "¿ Otra opción mas ?",
        "¿ O esto mejor ?",
        "¿ Quizas esto mejor ?",
        "¿ Esta cosa mejor ?",
        "¿ Deberia ?",
      ]
    };
  },
  props: {
    number: {
      type: Number,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
  },
  methods: {
    PasarTextoAlPadre(text2, id) {
      console.log("Salta el evento -> Text: ",text2)
      this.$emit("pasar-texto", [text2, id]);
    },
    placeholderFunction(number) {
      if(this.placeholder[number]){
        return this.placeholder[number];
      }else{
        return "¿ O esto ?"
      }
      
    }
  },
};
</script>