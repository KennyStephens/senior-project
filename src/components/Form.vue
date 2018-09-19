<template>
  <div id="form">
    <h1>Add Usability Tasks Here</h1>
    <form>
      <div class="form-group siteURL">
        <label class="text-light">{{ siteURL }}</label>
        <input type="text" class="form-control siteURL" id="siteURL" aria-describedby="emailHelp" @keyup="siteURLCheck">
      </div>
      <div class="form-group" id="taskInput">
        <label class="text-light">Task #1</label>
        <input type="text" class="form-control" aria-describedby="emailHelp" @keyup="inputCheck">
        <transition name="slide-fade">
        <i v-if="inputFilled" class="fas fa-check-circle input-check"></i>
        </transition>
      </div>
        <div class="form-group">
        <label class="text-light">Task #2</label>
        <input type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" @keyup="inputCheck">
      </div>
        <div class="form-group">
        <label class="text-light">Task #3</label>
        <input type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" @keyup="inputCheck">

      <div id="additional-items"></div>
    </div>

    <button id="add-button" @click="addTask"><i class="fas fa-plus-circle"></i></button>
    
    <button type="submit" class="btn btn-primary submit-button">Submit Tasks</button>
    </form>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      taskCounter: 3,
      siteURL: 'Site URL',
      inputFilled: false
    }
  },
  methods: {
    addTask(e) {

      this.taskCounter++
      // Grab form
      const addButton = document.querySelector('#additional-items');

      // Create new form-group div
      const formDiv = document.createElement('div');
      formDiv.classList.add('form-group');
      formDiv.style.marginTop = "1rem";
      
      // Create new label
      const formLabel = document.createElement('label');
      formLabel.classList.add('text-light');
      formLabel.innerText = `Task #${this.taskCounter}`;
      formDiv.appendChild(formLabel);

      // Create input
      const formInput = document.createElement('input');
      formInput.classList.add('form-control');
      formDiv.appendChild(formInput);

      addButton.appendChild(formDiv);

      e.preventDefault();
    },
    siteURLCheck() {
      const siteURL = document.getElementById('siteURL');
      if (siteURL.value.length > 5) {
        siteURL.style.border = '3px solid green';
      } else {
        siteURL.style.border = '2px solid red';
      }
    },
    inputCheck(e) {
      if(e.target.value.length > 0) {
        this.inputFilled = true;
      } else {
        this.inputFilled = false;
      }
    }
  }
}
</script>

<style lang="scss">
  h1 {
    color: aqua;
  }

  #form {
    width: 50%;
    text-align: left;
    background: #444;
    padding: 30px 40px;
    border-radius: 25px;
    max-height: 75%;
    overflow: auto;
  }

  #add-button {
    background: transparent;
    border: none;
    color: green;
    font-size: 1.7rem;
    display: block;
    float: right;
    opacity: .8;
   
    &:hover {
      opacity: 1;
    }
  }

  .input-check {
    color: green;
    float: right;
  }

  .submit-button {
    display: block;
    margin-top: 3em;
  }

  .siteURL {
    text-align: center;

    input {
    width: 50%;
    margin: 0 auto;

    &:focus {
      border-radius: 99px;
      border: 2px solid red;
    }
    }
  }

  input {
    border-radius: 99px;
    border: 2px solid red;
    width: 50%;
  }

  /* width */
::-webkit-scrollbar {
    width: 20px;
}

/* Handle */
::-webkit-scrollbar-thumb {
    background: aqua; 
    border-radius: 10px;
}

#taskInput {
  position: relative;

  .input-check {
    position: absolute;
    bottom: 10px;
    right: 5px;
  }

  .slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
}
</style>

