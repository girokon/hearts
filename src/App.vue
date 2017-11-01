<template>
  <div id="app">
    <HelloWorld/>
    <div style="margin-left: 30%">
      <ul>
        <li>1</li>
        <li>1</li>
        <li>1</li>
        <li>1</li>
        <li>1</li>
        <li>1</li>
      </ul>
      <particle-source/>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Particle from './components/Particle.vue'
import ParticleSource from './components/ParticleSource.vue'
import 'animate.css'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Particle,
    ParticleSource
  }
}
</script>

<style>

</style>
