<template>
  <div class="main-container">
    <div class="button-container">
      <button class="party-button" @click="initConfetti()">Let's Party!</button>
    </div>
    <div class="confetti-container">
      <canvas id="confetti-left" ref="canvas-confetti" class="confetti"></canvas>
    </div>
  </div>
</template>

<script>
import confetti from 'canvas-confetti';
export default {
  name: 'ConfettiExplosion',
  props: {
    msg: String
  },
  data() {
    return {
      confettiObj: null,
      clusterCount: 225, //make prop
    }
  },
  mounted() {
    this.initConfetti()
  },
  methods: {
    randomInRange(min, max) {
      return Math.random() * (max - min) + min;
    },
    initConfetti() {
      const canvasConfetti = this.$refs['canvas-confetti'];
      // document.body.appendChild(canvasConfetti);
      this.confettiObj = confetti.create(canvasConfetti, {
        resize: true,
        useWorker: true
      })

      // left side far
      this.confettiObj({
        particleCount: this.randomInRange(this.clusterCount, this.clusterCount + 33),
        spread: this.randomInRange(135, 155),
        colors: ['#007DBA', '#B1E4E3', '#1C8195', '#7A4282', '#E03C31', '#FFB81C'],
        startingVelocity: 22,
        scalar: 1.25,
        angle: 45,
        origin: {
          x: -0.1,
          y: 0.33
        },
      });
      // left side mid
      this.confettiObj({
        particleCount: this.randomInRange(this.clusterCount, this.clusterCount + 33),
        spread: this.randomInRange(55, 95),
        colors: ['#007DBA', '#B1E4E3', '#1C8195', '#7A4282', '#E03C31', '#FFB81C'],
        startingVelocity: 22,
        scalar: .85,
        angle: 45,
        origin: {
          x: -0.2,
          y: 0.5
        },
      });

      // right side big
      this.confettiObj({
        particleCount: this.randomInRange(this.clusterCount, this.clusterCount + 33),
        spread: this.randomInRange(155, 200),
        colors: ['#007DBA', '#B1E4E3', '#1C8195', '#7A4282', '#E03C31', '#FFB81C'],
        startingVelocity: 75,
        scalar: 1.25,
        angle: 135,
        origin: {
          x: 1,
          y: 0.33
        },
      });

      // left side mid
      this.confettiObj({
        particleCount: this.randomInRange(this.clusterCount, this.clusterCount + 33),
        spread: this.randomInRange(55, 95),
        colors: ['#007DBA', '#B1E4E3', '#1C8195', '#7A4282', '#E03C31', '#FFB81C'],
        startingVelocity: 22,
        scalar: .85,
        angle: 135,
        origin: {
          x: 1.2,
          y: 0.5
        },
      });
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.confetti-container {
  position: absolute;
  z-index: 3333;
  display: flex;
}
.confetti {
  height: 100vh;
  width: 100vw;
}

.button-container {
  position: absolute;
  width: 100vw;
  height: 10vh;
  padding-top: 3rem;
  z-index: 9999;
}
.party-button {
  padding: .75rem 1.75rem;
  background-color: dodgerblue;
  border-radius: 0.5rem;
  border: none;
  color: white;
  font-weight: 800;
  font-size: 1.5rem;
  cursor: pointer;
}
</style>
