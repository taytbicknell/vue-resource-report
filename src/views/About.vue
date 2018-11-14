<template>
  <div class="about">
    <h1>Resource Report</h1>
    <svg width="100%" height="700" font-family="sans-serif" font-size="10" text-anchor="middle"></svg>
  </div>
</template>

<style>
  html, body {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: Helvetica, Calibri, Roboto, Open Sans, sans-serif;
    -webkit-backface-visibility: hidden;
  }
  * {
    box-sizing: inherit;
  }
  h1 {
    text-align: center;
  }
  svg {
    margin:auto;
    display:circle;
  }

  .circle-overlay {
    font-size: 16px;
    border-radius: 10%;
    position: absolute;
    overflow: hidden;
    /*it's buggy with the foreignObject background right now*/
    /*background-color: rgba(255,255,255,0.5);*/
  }
  .circle-overlay__inner {
    text-align: center;
    width: 100%;
    height: 100%;
  }

  .hidden {
    display: none;
  }
  .node-icon--faded {
    opacity: 0.5;
  }
  .legend-size circle {
    fill: rgb(31, 119, 180);
  }
</style>

<script>
//import * as d3 from "d3";

export default {
  data: function() {
    return {
      data: {}
    };
  },
  created: function() {
    // Based loosely from this D3 bubble graph https://bl.ocks.org/mbostock/4063269
    // And this Forced directed diagram https://bl.ocks.org/mbostock/4062045
    let data = [{
      cat: 'temperature', name: 'current temperature', value: 50,
      icon: '../img/temp.png',
      desc: `
        Current Temperature in Crockett CA
      `
    }, {
      cat: 'humidity', name: 'current humidity', value: 50,
      icon: '../img/humidity.png',
      desc: `
        Current Humidity in Crockett CA
      `
    }, {
      cat: 'pressure', name: 'caurrent air pressure', value: 50,
      icon: '../img/pressure.png',
      desc: `
        Current Air Pressure in Crockett CA
    `
    }];

    
  }
};
</script>
