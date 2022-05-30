<script>
import components from 'vue';


export default {
  data() {
    return {
      translateWord: {},
      word: null,
      word_en: null,
      word_fr: null,
      userWord: "",
      won: null,
      showError: false,
      numberOfWin: 0,
      words: [
        {
          en: "fight",
          fr: "combat"
        },
        {
          en: "hello",
          fr: "bonjour"
        },
        {
          en: "creative",
          fr: "créatif"
        },
        {
          en: "work",
          fr: "travail"
        },
        {
          en: "fly",
          fr: "voler"
        },
        {
          en: "friend",
          fr: "ami"
        },
        {
          en: "new",
          fr: "nouveau"
        },
        {
          en: "catch",
          fr: "attraper"
        },
        {
          en: "go",
          fr: "aller"
        },
        {
          en: "learn",
          fr: "apprendre"
        },
        {
          en: "community",
          fr: "communauté"
        },
        {
          en: "école",
          fr: "school"
        }
      ],
      
    }
  },
  name: "Game",
  methods: {
    translateIsTrue () {
      console.log('Send Succesfully!');
      if (this.userWord.toLowerCase().replace(' ', '') == this.word_fr) {
        this.won = true
        console.log('is true')
      } else {
        this.showError = true;
      }
    },
    randomWord(){
      this.word = this.words[Math.floor(Math.random() * this.words.length)];
      this.word_en = this.word.en;
      this.word_fr = this.word.fr;
    },
    changeWonToFalse(){
      this.won = false;
      this.userWord = "";
      this.word = this.randomWord()
      this.numberOfWin++;
      this.showError = false;
    }
  },
  mounted: function(){this.randomWord()}
}
</script>

<template>
  <div class="flex flex-col justify-center items-center my-28">
    <div v-show="!won" class="flex flex-col justify-center items-center"> 
      <h1 id="title" class="text-6xl font-bold text-gray-900">The English Game</h1>
      <div class="flex space-y-3 flex-col items-center justify-center" id="game">
        <h3 class="text-4xl font-medium mt-3">Translate the word : <span class="font-bold text-indigo-500">{{ word_en }}</span></h3>
        <input type="text" v-model="userWord" class="border p-2 rounded focus:border-gray-900 focus:border"
          placeholder="What is the translation?" />
        <button type="submit" @click="translateIsTrue()"
          class="bg-indigo-500 text-white py-2 px-4 rounded hover:bg-indigo-400 transition-all duration-200">Send</button>
        <p>You have {{ numberOfWin }} win.</p>
        <p v-show="showError" class="bg-red-200 text-red-700 p-5 rounded border border-red-700 ">the translation is not the right one.</p>
      </div>
    </div>
    <h1 v-show="won" class="bg-indigo-200 p-10 text-indigo-700 rounded border border-indigo-700">You won!</h1>
    <button v-show="won" @click="changeWonToFalse" class="bg-indigo-500 text-white mt-4 hover:bg-indigo-400 transition-all duration-200 py-2 px-4 rounded ">Play Again</button>
  </div>
  
</template>

<style>
*::selection {
  background-color: rgba(160, 238, 255, 0.632);
}
</style>