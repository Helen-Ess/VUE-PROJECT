<script>
import { onUnmounted } from 'vue';

export default {
  props: ['msg'],
  data() {
    return {
      timergId: -1,
      currentTextIndex: 0,
      text: '',
      greetingText: [
        'Vue’s official documentation provides you with all information you need to get started.',
        'This project is served and bundled with Vite. The recommended IDE setup is VSCode + Volar',
        'Get official tools and libraries for your project: Pinia, Vue Router, Vue Test Utils, and Vue Dev Tools',
        'Got stuck? Ask your question on Vue Land, our official Discord server, or StackOverflow',
        'As an independent project, Vue relies on community backing for its sustainability',
      ]
    }
  },
  mounted(){
    this.text = this.greetingText[0];
    this.timerId =  setTimeout(this.changeText, 2000);
  },
  unmounted() {
    clearTimeout(this.timerId)
  },
  methods: {
    changeText() {
      clearTimeout(this.timerId)
      this.currentTextIndex++;
      if(this.currentTextIndex == this.greetingText.length) this.currentTextIndex = 0;
      this.text = this.greetingText[this.currentTextIndex];
      this.timerId =  setTimeout(this.changeText, 2000);
    }
  }
}
</script>

<template>
  <div class="greetings">
    <h1 class="green" @click="changeText">{{ msg }}</h1>
    <h3>
      {{ text }}
    </h3>
  </div>
</template>