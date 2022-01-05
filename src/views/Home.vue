<template>
  <div class="home overflow">
    <div class="row">
      <h1 class="m-3 mb-5" :class="bgColour">The Smiley Factory</h1>
    </div>
    <div class="row">
      <div class="col-6">
        <p>Step 1 : Select your color :</p>
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
        <p>Step 2 : Select your eyes :</p>
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
        <p>Step 3 : Select your nose :</p>
      </div>
      <div class="col-6">
        <div id="eyes">
          <select v-model="nose">
            <option v-for="myNose of noses" :key="myNose" :value="myNose">{{ myNose }}</option>
          </select>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <p>Step 4 : Select your mouse :</p>
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
        <p>Step 5 : Confirm your smiley :</p>
      </div>
      <div class="col-6">
        <div id="leave">
          <button type="button" class="btn btn-success" v-on:click="circle()">leave the factory</button>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <p>Step 6 : Create a new smiley :</p>
      </div>
      <div class="col-6">
        <div id="leave">
          <button type="button" class="btn btn-success" v-on:click="reload()">create</button>
        </div>
      </div>
    </div>

    <div class="circle mt-4" :class="bgColour">
      <div class="eye">
        <p :class="eye">{{ eye }}</p>
      </div>
      <div class="nose">
        <p :class="nose">{{ nose }}</p>
      </div>
      <div class="mouse">
        <p :class="mouse">{{ mouse }}</p>
      </div>
    </div>
    <div class="tapis"></div>
    <div id="canvas-container-div">
      <canvas id="canvas"></canvas>
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
      eyes: ['0  0', '__  __', '^  ^', 'x x'],
      nose: '|',
      noses: ['|', 'u', 'y', 'x'],
      mouse: '|________|',
      mouses: ['|________|', '________', 'O', '--------'],
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
.tapis {
  background-color: rgb(59, 29, 0);
  height: 1em;
  width: 100vw;
}

.overflow {
  overflow: hidden;
}
</style>
