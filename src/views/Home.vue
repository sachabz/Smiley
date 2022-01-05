<template>
  <div class="home">
    <div class="row">
      <div class="col-6">
        <h2 :class="bgColour">Step 1 : Select your color :</h2>
      </div>
      <div class="col-6">
        <div id="colorcircle">
          <select v-model="bgColour">
            <option v-for="myClass of classes" :key="myClass" :value="myClass">{{ myClass }}</option>
          </select>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <h2>Step 2 : Select your eyes :</h2>
      </div>
      <div class="col-6">
        <div id="eyes">
          <select v-model="eye">
            <option v-for="myEye of eyes" :key="myEye" :value="myEye">{{ myEye }}</option>
          </select>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <h2>Step 3 : Select your mouse :</h2>
      </div>
      <div class="col-6">
        <div id="mouses">
          <select v-model="mouse">
            <option v-for="myMouse of mouses" :key="myMouse" :value="myMouse">{{ myMouse }}</option>
          </select>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <h2>Step 4 : Confirm your smiley :</h2>
      </div>
      <div class="col-6">
        <div id="leave">
          <button v-on:click="circle()">leave the factory</button>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <h2>Step 5 : Create a new smiley :</h2>
      </div>
      <div class="col-6">
        <div id="leave">
          <button v-on:click="reload()">create</button>
        </div>
      </div>
    </div>

    <div class="circle mt-4" :class="bgColour">
      <div class="eye">
        <p :class="eye">{{ eye }}</p>
      </div>
      <div class="nose">
        <p>|</p>
      </div>
      <div class="mouse">
        <p :class="mouse">{{ mouse }}</p>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import { gsap } from "gsap";

export default {
  name: 'Home',
  data: () => {
    return {
      bgColour: 'yellow',
      classes: ['yellow', 'blue', 'purple'
      ],
      eye: '0  0',
      eyes: ['0  0', '__  __', '^  ^', 'D -'],
      mouse: '________',
      mouses: ['________/', '________', 'O'],
    };
  },
  components: {
  },
  methods: {
    circle: function () {
      gsap.fromTo('.circle', { opacity: 0 }, { opacity: 1, x: "100vw", duration: 4 });
      gsap.to(".circle", { duration: 4, rotation: 720 });
    },
    reload: function () {
      window.location.reload();
    }

  }
}
</script>

<style scoped lang="scss">
.circle {
  background-color: yellow;
  height: 10em;
  width: 10em;
  border-radius: 100%;
}

.colorcircle {
  transition: all 0.2s;
}

.yellow {
  background-color: yellow;
}

.blue {
  background-color: rgb(0, 195, 255);
}

.purple {
  background-color: rgb(255, 0, 255);
}
.eyes {
  background-color: blue;
  height: 2em;
  width: 2em;
  border-radius: 100%;
}
</style>
