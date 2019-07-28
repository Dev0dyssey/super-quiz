<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1>The Super Quiz</h1>
      </div>

    <hr>

    <div class="row">
      <div class="col-12 mx-auto">
        <transition name="turn" mode="out-in">
          <component :is="mode" @answered="answered($event)" @confirmed=" mode = 'Question' "></component>
        </transition>
      </div>
    </div>

    </div>
  </div>
</template>

<script>
  import Answer from './Answer';
  import Question from './Question';

  export default {
    components: {
      Answer,
      Question
    },

    data() {
      return {
        mode: 'Question'
      }
    },

    methods: {
      answered(isCorrect) {
        if(isCorrect) {
          this.mode = 'Answer';
        } else {
          this.mode = 'Question';
          alert('Wrong, please try again!');
        }
      }
    }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .turn-enter {
    transform: rotateY(0deg);
  }

  .turn-enter-active {
    animation: turn-in 0.5s ease-out forwards;
  }

  .turn-leave {
    transform: rotateY(0deg);
  }

  .turn-leave-active {
    animation: turn-out 0.5s ease-out forwards;
  }

  @keyframes turn-out {
    from {
      transform: rotateY(0deg);
    }
    to {
      transform: rotateY(90deg);
    }
  }

  @keyframes turn-in {
    from {
      transform: rotateY(90deg);
    }
    to {
      transform: rotateY(0deg);
    }
  }
</style>