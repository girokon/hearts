<template>
  <div class="container">
    <particle v-for="particle in particles" @after-leave="remove(particle)" :key="particle"></particle>
  </div>
</template>

<script>
  import Particle from './Particle.vue'

  export default {
    components: {
      Particle
    },
    data () {
      return {
        counter: 0,
        particles: []
      }
    },

    created () {
      this.add()

      setInterval(() => {
        this.add()
      }, 250)
    },
    methods: {
      add () {
        this.particles.push(this.counter)
        this.counter++
      },
      remove (particle) {
        let index = this.particles.findIndex(item => item === particle)
        this.particles.splice(index, 1)
      }
    }
  }
</script>

<style scoped>

</style>
