<template>
  <div class="m-auto">
    <h1 class="text-2xl text-center">DC Heros {{ herosCount }}</h1>
    <ul>
      <li class="flex justify-between" v-for="(hero, index) in dcHeros" :key="hero.name">
        <div>{{ hero.name }}</div>

        <!-- botao x para remover herois -->
        <button v-on:click="remove(index)">x</button> 
      </li>
    </ul>
    <form class="mt-10"
      @submit.prevent="addHero">

      <!-- input para colocar os herois -->
      <input class="border rounded" v-model="newHero" placeholder="Type Hero name here"/>

      <!-- botao para adicionar herois -->
      <button class="border rounded bg-gradient-to-r from-red-700 to-pink-500 text-white" type="submit">Add Hero</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {  
      newHero: "",
      dcHeros: [
        { name: "SuperGirl" },
        { name: "Flash" },
        { name: "Batman" },
        { name: "Arrow" },
        { name: "SuperMan" },
      ],
    };
  },
  computed: {
    herosCount() {
      return this.dcHeros.length;
    },
  },
  methods: {
    addHero() {
      if(this.newHero !== "")
      this.dcHeros.unshift({ name: this.newHero });
      this.newHero = "";
    },
    remove(index) {
      this.dcHeros = this.dcHeros.filter((hero, i) => i != index);
    },
  },
};
</script>

<style>

</style>