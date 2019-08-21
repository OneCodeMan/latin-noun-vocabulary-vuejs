<template>
  <div>
    <app-intro></app-intro>
    <app-nouns></app-nouns>
  </div>
</template>

<script>
import Intro from './components/Intro.vue';
import Nouns from './components/Nouns.vue';

export default {
  components: {
    'app-nouns': Nouns,
    'app-intro': Intro
  },
  data() {
    return {

    }
  },
  methods: {
    
  }
}
</script>

<style>
</style>
