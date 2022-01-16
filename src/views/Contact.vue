<template>
  <div class="contact">
    <h1>Contact</h1>
    <transition-group appear tag="ul" @before-enter="beforeEnter" @enter="enter">
      <li v-for="(icon,index) in icons" :key="icon.name" :data-index="index">
        <span class="material-icons">{{ icon.name }}</span>
        {{ icon.text }}
      </li>
    </transition-group>
  </div>
</template>

<script>
import { ref } from "vue";
import gsap from "gsap";
export default {
  setup() {
    const icons = ref([
      { name: "alternate_email", text: "email" },
      { name: "local_phone", text: "phone" },
      { name: "local_post_office", text: "post" },
      { name: "local_fire_department", text: "signal" },
    ]);

    const beforeEnter = (el) => {
      el.style.opacity = 0;
      el.style.transform = "translateY(100px)";
    };
    const enter = (el, done) => {
      gsap.to(el, {
        y: 0,
        opacity: 1,
        duration: 0.8,
        onComplete: done,
        delay: el.dataset.index * .2
      });
    };

    return { icons, beforeEnter, enter };
  },
};
</script>

<style scoped>
.contact ul {
  padding: 0;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;
  max-width: 400px;
  margin: 60px auto;
}
.contact li {
  display: grid;
  list-style-type: none;
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 1px 3px 5px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  line-height: 1.5em;
}
</style>