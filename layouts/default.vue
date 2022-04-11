<script lang="ts" setup>
import { gsap } from "gsap";
import { onMounted } from "vue";

onMounted(() => {
  gsap.to(".overlay", {
    // any properties (not limited to CSS)
    opacity: 0, // camelCase
    scale: 4,
    filter: "blur(20px)",
    filter: "invert(1)",
    duration: 2, // seconds
    display: "none",
    delay: 2,
    stagger: 0.05,
    ease: "power4.inOut",
  });
})
</script>

<template>
  <div >
     <img
          src="/afraid.jpg"
          alt=""
          class="fixed z-20 w-full h-screen object-contain overlay bg-white "
        />
    <slot />
    <div class="p-6">
      <ul class="flex gap-3 pt-96 justify-center w-full">
        <li><nuxt-link to="/imprint">Imprint</nuxt-link></li>
      </ul>
    </div>
    
  </div>
</template>

<style scoped></style>
