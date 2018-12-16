<template>
  <div id="app">
    <header>こたきの飼いたい！いきものずかん</header>
    <ul class="tab">
      <li class="tab__button" 
      v-for="(item, index) in tabItem" 
      v-on:click="changeTab(index)" 
      v-bind:class="{ 'is-active' : current == index }" 
      v-bind:key="index">{{ item.text }}</li>
    </ul>
    <creatureList v-bind:currentCategory="currentCategory"></creatureList>
    <referenceList></referenceList>
    <footer>@ KotakiMuseum All Rights Reserved.</footer>
  </div>
</template>

<script>
import creatureList from './components/creatureList'
import referenceList from './components/referenceList'

export default {
  name: 'App',
  components: {
    creatureList,
    referenceList
  },
  data() {
    return {
      current: 0,
      currentCategory: 'contemporary',
      tabItem: [
       { id: 0, category: 'contemporary', text: '現生生物編' },
       { id: 1, category: 'ancient', text: '古生物編' }
      ],
    }
  },
  methods: {
    changeTab(index) {
      this.current = index;
      this.currentCategory = this.tabItem[index].category;
    }
  }
}
</script>

<style src="./assets/scss/base.scss" lang="scss"></style>
<style src="./assets/scss/tab.scss" lang="scss"></style>

