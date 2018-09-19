<template>
  <div id="home">
    <transition name="fade">
      <h1 v-if="display.display">{{ title }}</h1>
    </transition>
    <transition name="fade">
      <button type="button" class="btn btn-outline-info" @click="displayItems" v-if="display.display">Get Started</button>
    </transition>
    <transition name="fade">
      <usb-form v-show="display.formDisplay"></usb-form>
    </transition>
</div>
</template>

<script>
import Form from "./Form.vue"
export default {
  components: {
      'usb-form': Form
  },
  data: function() {
    return {
      title: 'Welcome to Usable',
      display: {
        display: true,
        formDisplay: false
      }
    }
  },
  methods: {
    displayItems() {  
      setTimeout(()=> {
        this.display.formDisplay = true;
      }, 1000);
        
        this.display.display = false;
    }
  }
}
</script>

<style lang="scss" scoped>
/*--- Variables ---*/
$color-aqua: aqua;

  #home {
    text-align: center;

    h1 {
      color: $color-aqua;
    }

    /*--- Vue Animation Classes ---*/
    .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
    }

    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
      opacity: 0;
    }
  } 

  
</style>

