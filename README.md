# Star Rate Component

[![npm version](https://badge.fury.io/js/star-rate-component.svg)](https://badge.fury.io/js/star-rate-component)
[![Software License](https://img.shields.io/apm/l/vim-mode.svg)](https://github.com/thalysonrodrigues/star-rate-component/blob/master/LICENSE)

<p align="center">
    <a href="https://github.com/thalysonrodrigues/star-rate-component">
        <img src="./docs/star-rate.png" alt="Star Rate Component" title="Star Rate Component">
    </a>
</p>

> A simple component for VueJS. **Star Rate Component** is a component for [**VueJS**](https://vuejs.org/) for evaluating items through stars with or without punctuation. A customizable component in a simple and intuitive way with a sophisticated and good design.

## Installation

### Download (Zip)

Download this [link](https://github.com/thalysonrodrigues/star-rate-component/archive/v1.0.0.zip).

### Build

Clone this repository

```
$ git clone https://github.com/thalysonrodrigues/star-rate-component.git
```

### NPM

```
$ npm install --save star-rate-component@latest
```

## Get Started

### Basic usage

> **Note:** In your App.vue import

```vue
<template>
  <v-star-rate ref="component"></v-star-rate>
</template>

<script>
import StarRate from 'star-rate-component'

export default {
  name: 'App',
  components: {
    // name of component star rate
    'v-star-rate': StarRate
  }
}
</script>
```
<img width="150" src="./docs/gif/basic-usage.gif" alt="Basic usage" title="Basic Usage">

### Get value of rating

> Get a value of component by **$refs** in propertie "note"

```vue
<script>
(...)
export default {
  (...)
  methods: {
    show () { console.log(this.$refs.note4.note) }
  }
}
</script>
...
```

## Credits

- [Thalyson Alexandre Rodrigues de Sousa](https://github.com/thalysonrodrigues)

## License 

[MIT License](https://github.com/thalysonrodrigues/star-rate-component/blob/master/LICENSE) © 2018 Thalyson Rodrigues
