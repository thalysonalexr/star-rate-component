<template>
  <div id="evaluate-component" :class="'wrapper ' + size">
    <div :class="'box-' + display">
      <h1 class="title" :title="titleBox">
        {{ titleBox }}
      </h1>
    </div>
    <div :class="'box-' + display">
      <h2 class="note">
        {{ note }}
      </h2>
    </div>
    <div class="align-bottom">
      <div class="flex-box">
        <button @click="selectStar(5)" data-rate="5" class="star-box" :title="labels.perfect">
          <svg class="star" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/></svg>
        </button>
        <button @click="selectStar(4)" data-rate="4" class="star-box" :title="labels.great">
          <svg class="star" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/></svg>
        </button>
        <button @click="selectStar(3)" data-rate="3" class="star-box" :title="labels.good">
          <svg class="star" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/></svg>
        </button>
        <button @click="selectStar(2)" data-rate="2" class="star-box" :title="labels.bad">
          <svg class="star" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/></svg>
        </button>
        <button @click="selectStar(1)" data-rate="1" v-on:dblclick="noRate()" class="star-box" :title="labels.terrible">
          <svg class="star" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512"><path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/></svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Evaluate',
  props: {
    // color of star: rgb, rgba, hexadecimal
    starColor: {
      type: String,
      required: false,
      default: 'red'
    },
    borders: {
      type: Boolean,
      required: false,
      default: true
    },
    shine: {
      type: Boolean,
      required: false,
      default: false
    },
    display: {
      type: String,
      required: false,
      default: 'full', // simple, normal, full
      validator: function (value) {
        return ['simple', 'normal', 'full'].indexOf(value) !== -1
      }
    },
    // title the container of evaluate
    titleBox: {
      type: String,
      required: false
    },
    // notes for static component view
    result: {
      type: Array,
      required: false
    },
    // size in container evaluate
    size: {
      type: String,
      required: false,
      default: 'md',
      validator: function (value) {
        return ['sm', 'md', 'lg'].indexOf(value) !== -1
      }
    },
    // title for each level of stars
    labels: {
      type: Object,
      required: false,
      default: function () {
        return {
          terrible: 'terrible',
          bad: 'bad',
          good: 'good',
          great: 'great',
          perfect: 'perfect'
        }
      },
      validator: function (object) {
        return 'terrible' in object && 'bad' in object && 'good' in object && 'great' in object && 'perfect' in object
      }
    }
  },
  data () {
    return {
      note: 0
    }
  },
  methods: {
    selectStar (value) {
      // set animation
      $(this.$el.querySelectorAll('.star')).removeClass('star-color-selected')
      $(this.$el.querySelectorAll('.flex-box > .star-box:hover .star, .flex-box > .star-box:hover ~ .star-box .star')).addClass('star-color-selected')
      // set value for note
      this.note = value
    },
    noRate () {
      $(this.$el.querySelectorAll('.star')).removeClass('star-color-selected')
      this.note = 0
    },
    // exception for invalid argument
    InvalidNoteException (message) {
      this.message = message
      this.name = 'InvalidNoteException'
    },
    selectStarByData (note) {
      // select elements
      $(this.$el.querySelectorAll(`.star-box[data-rate="${note}"] .star, .star-box[data-rate="${note}"] ~ .star-box .star`)).addClass('star-color-selected')
    },
    disableStar () {
      // disable buttons
      $(this.$el.querySelectorAll('.star-box')).attr('disabled', true)
    },
    isValid (value) {
      const invalid = (n) => n < 0 || n > 5

      if (value.map(invalid).includes(true)) {
        throw new this.InvalidNoteException('Assessment grades should be between 0 and 5')
      }
    },
    average (value) {
      const sum = (x, y) => x + y
      return (value.reduce(sum) / value.length).toFixed(1)
    },
    calc () {
      if (this.$props.result !== undefined) {
        this.disableStar()

        if (this.$props.result.length > 0) {
          this.isValid(this.$props.result)

          let note = this.average(this.$props.result)

          if (note % 1 === 0) {
            note = Math.round(note)
          }

          this.selectStarByData(Math.round(note))

          this.note = note
        }
      }
    }
  },
  mounted () {
    this.$nextTick(function () {
      this.calc()
    })
  },
  watch: {
    result (val, oldVal) {
      this.calc()
    }
  }
}
</script>

<style scoped>

.wrapper{
  border-radius: 7px;
  border: 1px solid #dddddd;
  box-shadow: 1px 1px 2px #dbdbdb;
  margin: 1%;
  padding: 4% 2%;
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
  justify-content: center;
  background-blend-mode: lighten;
  background-color: #fcfcfc;
}

@media all and (min-width: 600px) {
  .wrapper{
    padding-top: 3%;
    padding-bottom: 3%;
  }
}

@media all and (min-width: 1280px) {
  .wrapper{
    padding-top: 2%;
    padding-bottom: 2%;
  }
}

.box-simple{ display: none; }
.box-normal h1{ display: none; }

.box-full{
  width: 100%;
  display: flex;
  align-self: center;
  justify-content: center;
}

.sm{ width: 120px; }
.md{ width: 180px; }
.lg{ width: 220px; }

.sm .title{ font-size: 1em; }
.md .title{ font-size: 1.3em; }
.lg .title{ font-size: 1.6em; }

.sm .note{ font-size: 3em; }
.md .note{ font-size: 5em; }
.lg .note{ font-size: 6em; }

.title, .note{
  font-family: sans-serif;
  font-smoothing: antialiased;
  font-smoothing: grayscale;
  color: #2c3e50;
  text-align: center;
  margin-bottom: 20%;
}

.align-bottom{
  display: flex;
  align-items: flex-end;
}

.flex-box{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-end;
  direction: rtl;
}

.flex-box > .star-box:hover .star,
.flex-box > .star-box:hover ~ .star-box .star{ fill: #fff570!important; }

.flex-box > .star-box:hover,
.flex-box > .star-box:hover ~ .star-box{
  transform: scale(1.2, 1.2);
  -webkit-transform: scale(1.2, 1.2);
}

.star-color-selected{
  fill: #fff83f!important;
  transform: scale(1.2, 1.2);
  -webkit-transform: scale(1.2, 1.2);
  animation: shine 300ms infinite;
  -webkit-animation: shine 300ms infinite;
}

@keyframes shine{
  0%{fill: #fffa70;}
  25%{fill: #fff84c;}
  50%{fill: #fff62d;}
  75%{fill: #fff519;}
  100%{fill: #fff405;}
}

@-webkit-keyframes shine{
  0%{fill: #fffa70;}
  25%{fill: #fff84c;}
  50%{fill: #fff62d;}
  75%{fill: #fff519;}
  100%{fill: #fff405;}
}

.star{
  width: 100%;
  fill: #dbdbdb;
}

.star-box{
  width: 16%;
  cursor: pointer;
  transition: transform 300ms ease;
  -webkit-transition: transform 300ms ease;
}

button.star-box{ background-color: transparent; }

button.star-box{ outline: none; }
</style>
