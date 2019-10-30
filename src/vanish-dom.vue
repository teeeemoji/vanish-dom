<template>
  <div class="vanish-dom" ref="wrapper">
    <div class="slot-wrapper" ref="slotWrapper">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import snapFadeAway from 'snap-fade-away'

const noop = function() {
  return true
}
/**
 * This is an Vue Component of creating a reusable particle effects animate, it will let slot vanishe, just like Thanos snapping finger.
 * Using [snap-fade-away](https://github.com/imcuttle/snap-fade-away)
 * @version 1.0.0
 * @author [Teeeemoji](https://github.com/teeeemoji)
 * @since Version 1.0.0
 */
export default {
  name: 'VanishDom',
  props: {
    /**
     * hook before vanish animate start
     * @version 1.0.0
     * @since Version 1.0.0
     * @return {Boolean | Promise<Boolean>} if returns true/Promise.resolve(true), vanish animate will start, else if return false/Promise.resolve(false), vanish animate will not start;
     */
    beforeVanish: {
      type: Function,
      default: noop
    },
    /**
     * hook after vanish animate end, after this hook invoked, *data.vanished* will be set to true
     * @version 1.0.0
     * @since Version 1.0.0
     */
    afterVanish: {
      type: Function,
      default: noop
    }
  },
  data() {
    return {
      vanished: false
    }
  },
  methods: {
    /**
     * start vanish animate
     *
     * @public
     * @version 1.0.0
     * @since Version 1.0.0
     * @returns {Promise<void>}
     */
    vanish: function() {
      // if (await this.beforeVanish()) {
      //   await snapFadeAway(this.$refs.wrapper)
      //   await this.afterVanish()
      //   this.vanished = false
      // }
      return snapFadeAway(this.$refs.slotWrapper, {
        debug: false,
        duration: '3s',
        relativeElem: this.$refs.wrapper
      })
    }
  }
}
</script>

<style lang="less">
canvas {
  z-index: 10000;
}

.vanish-dom {
  position: relative;
  display: block;
}
</style>
