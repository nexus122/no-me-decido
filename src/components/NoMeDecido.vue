<template>
  <section class="NoMeDecido">
    <h1>{{ title }}</h1>    
    <p class="description">Escribe tus opciones, pulsa en aleatorizar y disfruta de no tener que pensar</p>
    <ul>
      <li> Pulsa <i class="fa-solid fa-plus"></i> para crear una tarjeta nueva</li>
      <li> Pulsa <i class="fa-solid fa-shuffle"></i> para que la web tome esa dificil decision por ti</li>
    </ul>
    <div class="cardSection">
      <section v-for="card in cards" :key="card.number">
        <Card v-if="!winer || winer == card.id" :text=card.text :number=card.id v-on:pasar-texto="haLlegadoElTexto"></Card>
      </section>
      
    </div>
    <div class="controls">
        <button class="btn crear" @click="crear()"><i class="fa-solid fa-plus"></i></button>
        <button class="btn aleatorio" @click="aleatorio()"><i class="fa-solid fa-shuffle"></i></button>
    </div>
  </section>
</template>

<script>
import Card from "../components/Card.vue";

export default {
  name: "NoMeDecido",
  components: {
    Card,
  },
  data() {
    return {
      title: "No me p*** decido",
      winer: null,
      cards: [
        {
          id:1,
          text: "",
        },
        {
          id:2,
          text: "",
        }
      ],
    };
  },
  methods: {
    crear() {
      this.cards.push({
        id: this.cards.length + 1,
        text: "",
      });
      this.winer = null;
    },
    aleatorio() {
      var min = 1;
      var max = this.cards.length+1;
      var resp = Math.floor(Math.random() * (max - min)) + min;
      this.winer = resp;
    },
    haLlegadoElTexto(param) { // <-- Definimos la funcion que saltara al recibir la información
      console.log("Ha llegado el texto: ", param);
      this.cards.forEach((card) => {
        if (card.id == param[1]) {
          card.text = param[0];
        }
      });
    }
  },
};
</script>

<style scoped>
h1 {
  font-size: 3em;
  font-family: "Bebas Neue", cursive;
  color: white;
  text-align: center;
  width: 100%;
  margin: 0px;
  padding: 0px;
  margin-top: 1em;
}
.description{
  padding-bottom: 1em;
}
.cardSection {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding-bottom: 1em;
}

.btn{
    width: 25%;
    border: 0;
    background: transparent;
    color: white;
    cursor: pointer;
    border: 1px solid white;
    border-radius: 1em;
    padding: 1em;
}
.btn:hover{
    width: 25%;
    border: 0;
    background: white;
    color: black;
    cursor: pointer;
    border: 1px solid black;
    border-radius: 1em;
    padding: 1em;
}
ul{
  list-style: none;
  text-align: start;
}
</style>