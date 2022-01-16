<template>
  <div class="about">
    <transition 
    appear 
    name="fade"
    @before-enter="beforeEnter"
    @enter="enter"
    >
      <h1>This is an about page</h1>
    </transition>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis, vitae!
      Quae, facilis, excepturi dolores unde quibusdam consequatur delectus
      reiciendis a ducimus modi maxime rem fugiat? Omnis quos deleniti accusamus
      quod.
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis, vitae!
      Quae, facilis, excepturi dolores unde quibusdam consequatur delectus
      reiciendis a ducimus modi maxime rem fugiat? Omnis quos deleniti accusamus
      quod.
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis, vitae!
      Quae, facilis, excepturi dolores unde quibusdam consequatur delectus
      reiciendis a ducimus modi maxime rem fugiat? Omnis quos deleniti accusamus
      quod.
    </p>
  </div>
</template>

<script>

import gsap from 'gsap'

export default {
  setup() {
      const beforeEnter = (el) => {
        el.style.transform = 'translateY(-60px)'
        el.style.opacity = 0
      }
      const enter = (el) => {
        gsap.to(el, {
          y: 0,
          opacity: 1,
          duration: 2,
          ease: 'bounce.out'
        })
      }


      return { beforeEnter, enter }
  },
}
</script>
<style>
  .about {
    max-width: 600px;
    margin: auto;
  }
</style>

