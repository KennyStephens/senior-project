<template>
  <div id="main-wrapper">
    <usb-navbar></usb-navbar>
      <div id="home">
        <div>
          <transition name="fade">
            <h1 v-if="display.display">{{ title }}</h1>
          </transition>
          <transition name="fade">
            <button type="button" class="btn btn-outline-info" @click="displayItems" v-if="display.display">Get Started</button>
          </transition>
      </div>
 

    <!-- Form -->
    <transition name="fade">
      <usb-form v-show="display.formDisplay"></usb-form>
    </transition>
</div>
  </div>

</template>

<script>
// Imports
import Form from "./Form.vue"
import Navbar from "./Navbar.vue"

export default {
  components: {
      'usb-form': Form,
      'usb-navbar': Navbar
  },
  data: function() {
    return {
      title: 'Welcome to Usabl',
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
    display: flex;
    height: 100vh;
    width: 100vw;
    align-items: center;
    justify-content: center;
    text-align: center;

    h1 {
      color: $color-aqua;
    }

    button {
      border: aqua 1px solid;
      color: aqua;

      &:hover {
        background: aqua;
        color: #333;
      }
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

