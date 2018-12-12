<template>
  <div class="accordion">
    <transition name="accordion" v-on:before-enter="beforeEnter" v-on:enter="enter" 
    v-on:before-leave="beforeLeave" v-on:leave="leave">
      <div class="accordion__body" v-show="isOpen">
        <slot name="body"></slot>
      </div>
    </transition>
    <button class="accordion__button" 
    v-bind:class="{ 'is-open' : isOpen }" 
    v-on:click="toggle">{{ buttonText }}</button>
  </div>
</template>

<script>
export default {
  name: 'accordion',
  data () {
    return {
      isOpen: false,
      buttonText: 'このいきものをみるよ'
    }
  },
  methods: {
    toggle() {
      this.isOpen = !this.isOpen;
      if(this.isOpen) {
        this.buttonText = 'もうみないよ'
      } else {
        this.buttonText = 'このいきものをみるよ'
      }
    },
    beforeEnter(e) {
      e.style.height = '0';
    },
    enter(e) {
      e.style.height = e.scrollHeight + 'px';
    },
    beforeLeave(e) {
      e.style.height = e.scrollHeight + 'px';
    },
    leave(e) {
      e.style.height = '0'
    }
  }
}
</script>

<style src="../assets/scss/accordion.scss" lang="scss"></style>
