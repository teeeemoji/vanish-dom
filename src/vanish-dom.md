VanishDom example:

```vue
<template>
  <transition type="animation">
    <div class="demo">
      <img
        width="300"
        height="300"
        src="https://www.diyimei.net/upload/2018/1517149952130571.jpg"
        alt=""
      />
      <vanish-dom
        ref="vanish"
        style="float:left"
        :before-vanish="beforeVanish"
        :after-vanish="afterVanish"
      >
        <img
          width="300"
          height="300"
          src="https://img.wowoqq.com/allimg/171018/1-1G01PQ445-52.jpg"
          alt=""
        />
      </vanish-dom>
      <button @click="vanish">
        vanish
      </button>
    </div>
  </transition>
</template>

<script>
export default {
  data() {
    return {}
  },
  methods: {
    beforeVanish: function() {
      console.log('vanish animation will start right now')
      return new Promise(function(resolve) {
        setTimeout(function() {
          resolve(true)
        }, 1000)
      })
    },
    afterVanish: function() {
      console.log('vanish animation ended')
    },
    vanish: function() {
      this.$refs.vanish.vanish().then(function() {
        console.log('vanished')
      })
    }
  }
}
</script>
```
