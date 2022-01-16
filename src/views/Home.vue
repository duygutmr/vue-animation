<template>
  <div class="home">
    <transition name="toast">
    <Toast v-if="showToast" />

    </transition>
    <Todos @badValue="triggerTost" />
   
  </div>
</template>

<script>
// @ is an alias to /src
import Todos from "@/components/Todos.vue";
import Toast from "@/components/Toast.vue";
import { ref } from "vue";
export default {
  name: "Home",
  components: {
    Todos,
    Toast,
  },
  setup() {
    const showToast = ref(false);

    const triggerTost = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000);
    };

    return { showToast, triggerTost };
  },
};
</script>
<style>
  .fade-enter-from{
    opacity: 0;
  }

  .fade-enter-active,
  .fade-leave-active {
    transition: all .5s ease;
  }

  .fade-leave-to {
    opacity: 0;
  }

  .toast-enter-active {
    animation: wobble .5s ease;
  }
   .toast-leave-from {
    opacity: 1;
    transform: translateY(0);
  }
  .toast-leave-to {
    opacity: 0;
    transform: translateY(-60px);
  }
  .toast-leave-active {
    transition: all .3s ease;
  }

  @keyframes wobble {
    0% {
      opacity: 0;
      transform: translateY(-60px);
    }
    50%{
      opacity: 1;
      transform: translateY(0);
    }
    60%{ transform: translateX(8px); }
    70%{ transform: translateX(-8px); }
    80%{ transform: translateX(4px); }
    90%{ transform: translateX(-4px); }
    100%{ transform: translateX(0); }
  }
</style>
