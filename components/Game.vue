<script>
import components from 'vue';


export default {
  data() {
    return {
      translateWord: {},
      word: null,
      word_en: null,
      word_fr: null,
      userWord: null,
      won: null,
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
          fr: "lutte"
        }
      ],
      
    }
  },
  name: "Game",
  methods: {
    translateIsTrue () {
      console.log('Send Succesfully!');
      if (this.userWord == this.word_fr) {
        this.won = true
        console.log('is true')
      }
    },
    randomWord(){
      this.word = this.words[Math.floor(Math.random() * this.words.length)];
      this.word_en = this.word.en;
      this.word_fr = this.word.fr;
    }
  },
  mounted: function(){this.randomWord()}
}
</script>

<template>
  <div class="flex flex-col justify-center items-center my-28">
    <div v-show="!won"> 
      <h1 id="title" class="text-6xl font-bold text-gray-900">The English Game</h1>
      <div class="flex space-y-3 flex-col items-center justify-center" id="game">
        <h3 class="text-4xl font-medium mt-3">Translate the word : <span>{{ word_en }}</span></h3>
        <input type="text" v-model="userWord" class="border p-2 rounded focus:border-gray-900 focus:border"
          placeholder="What is the translation?" />
        <button type="submit" @click="translateIsTrue()"
          class="bg-gray-900 text-white py-2 px-4 rounded hover:bg-gray-800 transition-all duration-200">Send</button>
      </div>
    </div>
    <h1 v-show="won" class="font-extrabold text-green-700">You won!</h1>
  </div>
  
</template>

<style>
</style>