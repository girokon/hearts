<template>
  <div class="container">
    <transition appear
                name="custom"
                enter-active-class="animated fadeIn zoomIn"
                leave-active-class="animated fadeOut"
                @after-leave="afterLeave"
                @enter="enter"
                @leave="leave"
    >
      <img :src="heart" class="sprite" v-if="visible"/>
    </transition>
  </div>
</template>

<script>
  import heart from './like.svg'
  import Velocity from 'velocity-animate'

  export default {
    props: {
      ttl: {
        type: Number,
        // in ms
        default: 1000
      }
    },
    mounted () {
      this.randomDeg = Math.round(Math.random() * 100) + 1
      setTimeout(() => {
        this.visible = false
      }, this.ttl)
    },
    data () {
      return {
        heart,
        visible: true,
        randomDeg: 0,
        toY: 100,
        toX: Math.round(Math.random() * 60) - 30
      }
    },
    methods: {
      afterLeave () {
        this.$emit('after-leave')
      },
      enter (el, done) {
        Velocity(el, {
          translateY: `-${this.toY - 0.25 * this.toY}px`,
          translateX: `${this.toX}px`,
          rotateZ: `${this.toX}deg`
        }, {
          complete: done,
          duration: this.ttl,
          easing: 'linear'
        })
      },
      leave (el, done) {
        //        Velocity(el, {rotateZ: '100deg'}, {loop: 2})
        Velocity(el, {
          //          rotateZ: `-${this.randomDeg}deg`,
          translateY: `-${this.toY}px`
        }, {
          complete: done,
          duration: this.ttl / 2,
          easing: 'linear'
        })
      }
    }
  }
</script>

<style scoped>
  .sprite {
    width: 25px;
    height: 25px;
  }

  .container {
    position: absolute;
  }
</style>
