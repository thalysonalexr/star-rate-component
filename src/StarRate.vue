<template>
  <div
    id="star-rate"
    class="wrapper"
    :class="(borders ? 'border ': '') + size"
    :style="'background-color: ' + colorBox">
    <div
      v-if="titleBox"
      :class="'box-' + display">
      <h1
        class="title"
        :title="titleBox"
        :style="'color: ' + colorText">
        {{ titleBox }}
      </h1>
    </div>
    <div :class="'box-' + display">
      <div class="wrapper-note">
        <h2
          class="note"
          :style="'color: ' + colorText">
          {{ note }}
        </h2>
      </div>
    </div>
    <div class="align-bottom">
      <div class="flex-box">
        <button
          @click="selectStar(5)"
          data-rate="5"
          class="star-box"
          :title="labels.perfect">
          <svg
            :style="'fill: ' + defaultColorStar"
            class="star"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 576 512">
            <path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/>
          </svg>
        </button>
        <button
          @click="selectStar(4)"
          data-rate="4"
          class="star-box"
          :title="labels.great">
          <svg
            :style="'fill: ' + defaultColorStar"
            class="star"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 576 512">
            <path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/>
          </svg>
        </button>
        <button
          @click="selectStar(3)"
          data-rate="3"
          class="star-box"
          :title="labels.good">
          <svg
            :style="'fill: ' + defaultColorStar"
            class="star"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 576 512">
            <path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/>
          </svg>
        </button>
        <button
          @click="selectStar(2)"
          data-rate="2"
          class="star-box"
          :title="labels.bad">
          <svg
            :style="'fill: ' + defaultColorStar"
            class="star"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 576 512">
            <path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/>
          </svg>
        </button>
        <button
          @click="selectStar(1)"
          data-rate="1"
          v-on:dblclick="noRate()"
          class="star-box"
          :title="labels.terrible">
          <svg
            :style="'fill: ' + defaultColorStar"
            class="star"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 576 512">
            <path d="M259.3 17.8L194 150.2 47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5 105.7-103c19-18.5 8.5-50.8-17.7-54.6L382 150.2 316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0z"/>
          </svg>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'StarRate',
  props: {
    colorBox: {
      type: String,
      required: false,
      default: '#fcfcfc'
    },
    colorText: {
      type: String,
      required: false,
      default: ''
    },
    defaultColorStar: {
      type: String,
      required: false,
      default: '#dbdbdb'
    },
    colorStar: {
      type: String,
      required: false,
      default: ''
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
      default: 'normal',
      validator: (value) => ['simple', 'normal'].indexOf(value) !== -1
    },
    titleBox: {
      type: String,
      required: false,
      validator: (value) => value.length >= 1 && value.length <= 25
    },
    result: {
      type: Array,
      required: false,
      validator: (arr) => !arr.map((x) => !isNaN(parseFloat(x)) && isFinite(x) && x >= 0 && x <= 5).includes(false)
    },
    size: {
      type: String,
      required: false,
      default: 'md',
      validator: (value) => ['sm', 'md', 'lg'].indexOf(value) !== -1
    },
    labels: {
      type: Object,
      required: false,
      default: () => ({
        terrible: 'terrible',
        bad: 'bad',
        good: 'good',
        great: 'great',
        perfect: 'perfect'
      }),
      validator: (object) => !['terrible', 'bad', 'good', 'great', 'perfect'].map((x) => x in object).includes(false)
    }
  },
  data () {
    return {
      note: 0
    }
  },
  methods: {
    selectStar (value) {
      const elements = this.$el.querySelectorAll('.flex-box > .star-box:hover .star, .flex-box > .star-box:hover ~ .star-box .star')

      this.$el.querySelectorAll('.star').forEach((el) => {
        el.classList.remove('star-color-selected')
      })

      elements.forEach((el) => {
        el.classList.add('star-color-selected')
      })

      if (this.shine) {
        this.setShineAnimation(elements)
      }

      this.note = value
    },
    setShineAnimation (elements) {
      this.disableShineAnimation()

      elements.forEach((el) => {
        el.classList.add('shine')
      })
    },
    disableShineAnimation () {
      this.$el.querySelectorAll('.star').forEach((el) => {
        el.classList.remove('shine')
        el.classList.remove('star-color-selected')
      })
    },
    noRate () {
      this.disableShineAnimation()
      this.note = 0
    },
    InvalidNoteException (message) {
      this.message = message
      this.name = 'InvalidArgumentException'
    },
    selectStarByData (note) {
      const elements = this.$el.querySelectorAll(`.star-box[data-rate="${note}"] .star, .star-box[data-rate="${note}"] ~ .star-box .star`)

      if (this.shine) {
        this.setShineAnimation(elements)
      }

      elements.forEach((el) => {
        el.classList.add('star-color-selected')
      })
    },
    disableStar () {
      this.$el.querySelectorAll('.star-box').forEach((el) => {
        el.setAttribute('disabled', true)
      })
    },
    isValid (value) {
      if (value.map((n) => n < 0 || n > 5).includes(true)) {
        throw new this.InvalidNoteException('Assessment grades should be between 0 and 5.')
      }
    },
    average (value) {
      return (value.reduce((x, y) => x + y) / value.length).toFixed(1)
    },
    calc () {
      if (this.result !== undefined) {
        this.disableStar()

        if (this.result.length > 0) {
          this.isValid(this.result)

          let note = this.average(this.result)

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
    this.$nextTick(() => this.calc())
  },
  watch: {
    result () {
      this.calc()
    }
  }
}
</script>

<style scoped>
@charset "utf-8";
@import url('https://fonts.googleapis.com/css?family=Open+Sans&display=swap');

*{
  margin: 0;
  padding: 0;
  border: 0;
  outline: none;
  box-sizing: border-box;
}

.wrapper{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 5px;
  background-blend-mode: lighten;
  background-color: #fcfcfc;
}

.border{
  border-radius: 7px;
  border: 1px solid #dddddd;
  box-shadow: 1px 1px 2px #dbdbdb;
}

@media all and (min-width: 600px) {
  .wrapper{
    padding-top: 2%;
    padding-bottom: 2%;
  }
}

@media all and (min-width: 1280px) {
  .wrapper{
    padding-top: 1%;
    padding-bottom: 1%;
  }
}

.box-simple{ display: none; }

.sm{ width: 120px; }
.md{ width: 180px; }
.lg{ width: 220px; }

.sm .title{ font-size: 1em; }
.md .title{ font-size: 1.3em; }
.lg .title{ font-size: 1.6em; }

.sm .note{ font-size: 3em; }
.md .note{ font-size: 5em; }
.lg .note{ font-size: 6em; }

.sm .star-box{ width: 20px; }
.md .star-box{ width: 30px; }
.lg .star-box{ width: 35px; }

.title{ font-weight: 0!important; }
.note{ font-weight: bold; }

.title, .note{
  margin: 0;
  font-family: 'Open Sans', sans-serif;
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
}

.shine{
  animation: shine 300ms infinite;
  -webkit-animation: shine 300ms infinite;
}

@keyframes shine{
  0%{fill: #fffa70;}
  25%{fill: #fff84c;}
  50%{fill: #ffd94d;}
  75%{fill: #ffcd17;}
  100%{fill: #ffc905;}
}

@-webkit-keyframes shine{
  0%{fill: #fffa70;}
  25%{fill: #fff84c;}
  50%{fill: #ffd94d;}
  75%{fill: #ffcd17;}
  100%{fill: #ffc905;}
}

.star{
  width: 100%;
  fill: #dbdbdb;
}

.star-box{
  width: 35px;
  cursor: pointer;
  transition: transform 300ms ease;
  -webkit-transition: transform 300ms ease;
}

button.star-box{
  border: none;
  outline: none;
  background-color: transparent;
}
</style>
