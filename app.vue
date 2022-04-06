<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { ref, onMounted } from "vue";
const color = ["text-black", "text-white", "text-stone-400"];
const background = ["bg-white", "bg-stone-400", "bg-black"];
const images = ["/image1.jpg", "/image2.jpg", "/image3.jpg"];
const emptyImage = ref(["/image1.jpg", "/image2.jpg", "/image3.jpg", "/image1.jpg", "/image2.jpg", "/image3.jpg"]);
var num = 0;
let single = ref(color[num + 1]);
let singlebg = ref(background[num + 1]);
// let image = ref(images[num+1])
var mainInterval = setInterval(() => {
  
  // emptyImage.value.push(images[num]);
  single.value = color[num];
  singlebg.value = background[num];
  // image.value = images[num]
  num++;
  if (num >= color.length) {
    num = 0;
  }
}, 5000);
function stopInterval() {
  clearInterval(mainInterval);
}
gsap.registerPlugin(ScrollTrigger); 


onMounted(() => {
  var sections = gsap.utils.toArray('img');

  gsap.from("p, h1, .images", {
    y: 20, // any properties (not limited to CSS)
    opacity: 0, // camelCase
    duration: 1, // seconds
    delay: 2,
    stagger: 0.05,
    ease: "power2.inOut",
  });
  gsap.to(".overlay", {
     // any properties (not limited to CSS)
    opacity: 0, // camelCase
    duration: 1, // seconds
    display: "none",
    delay: 1,
    stagger: 0.05,
    ease: "power4.inOut",
  });
  // sections.forEach((section) => {
  // gsap.from(section, {
  //   scrollTrigger: {
  //     trigger: section,
  //     start: "center center",
  //     pin: true,
  //     scrub: true,
  //     // pinType: "fixed",
  //     },// any properties (not limited to CSS) // camelCase
  //   opacity: 0,
  //   duration: 1, // seconds
  //   ease: "expo.out",
  // });
  // })
});
</script>

<template>
  <div class="relative">
    <Head>
      <Title>TROUBLE Inc.</Title>
      <Body
        :class="single + ` ` + singlebg"
        class="transition-colors duration-[5000ms]"
      ></Body>
    </Head>
    <img src="/afraid.jpg" alt="" class="fixed z-20 w-full h-screen object-cover overlay">
    <div class="p-6 relative z-10 lg:grid grid-cols-2 gap-20 ">
      <div class="">
        <div class="text-6xl">
          <h1 class="" @click="test">
            Who is afraid of white, black, and beige?
          </h1>
          <p  class="text-sm my-2 font-normal tracking-widest">TROUBLE Inc.</p>
        </div>
        <p class="text-6xl my-10">28.4 — 3.7.2022</p>
        <p>Galerie</p>
        <p>Gisela Clement</p>
        <p>Galeriehaus</p>
        <p class="pt-4">Opening April 28, 2022 at 6pm.</p>
        <p>The exhibition takes place inside the Project Space.</p>
        <p class="pt-4">The artist collective will be present.</p>
        <p>
          On the occasion of the opening there will be an artist talk in English
          led by Prof. Dr. Claudia Jarzebowski.
        </p>
        <p class="pt-4">Lotharstraße 104</p>
        <p>53115 Bonn</p>
        <p>galerie-clement.de</p>
      </div>
      <div class="intro">
        <p>
          A photographic examination of identity, gender and racism is subjected
          to a complex reinterpretation.
        </p>
        <p>
          What role does skin color plays and how does it still impact our
          feelings and perceptions when making decisions in human relationships?
        </p>
        <p>
          How has the political policies within the system build on color
          identity has been a pivotal validation on ethnic, racial oppression
          and segregation through discourses around value, taste, culture,
          methodology and the deployment of color. While race and class are
          still defined in black and white in large parts of society, a new
          consciousness shaped by social media and digitalization is
          increasingly shifting these conditional boundaries of gender and
          identity towards new collectivity and solidarity.
        </p>
        <p>
          As a black woman who has worked in the fashion industry all her life
          as a model and fashion influencer, Michelle Elie is confronted with
          questions about age, body and skin color as well as norms and
          stereotypes on a daily basis. The first fictional portraits were
          created in this area of ​​tension between our own experiences and the
          lack of representation of the other in our collective memory.
        </p>
        <p class="pt-4">
          Michelle Elie (the model-cum-designer-cum-fashion fixture) and Troi
          Ollivierre (the hair and make-up artist) have always been sort of
          creative soulmates. Since their first connection in downtown New York
          City in the '90s, the duo have been creating together, both for work
          and play. Add in Michelle's husband, acclaimed art director and artist
          Mike Meiré, and you have TROUBLE Inc.
        </p>
        <p class="pt-4">
          In moments when so many people feel the inequality and injustice of
          the ruling systems, it is about a strong conviction in who you are and
          what you identify with. Without discrimination or exclusion. Who's
          afraid of black, white and beige?
        </p>
        <p class="pt-4 text-sm my-2 font-normal tracking-widest">TROUBLE Inc.</p>
      </div>
    </div>
    <div class="w-full lg:flex lg:fixed bottom-0 left-0  gap-6 p-6  ">
      <div class=" w-full rounded overflow-hidden  images " v-for="image in emptyImage" :key="image">
        <img
          :src="image"
          alt=""
          class=" lg:h-full  py-3 lg:p-0 object-cover saturate-0 hover:filter-none opacity-50 hover:opacity-100 transition-all"
        />
      </div>
    </div>
  </div>
</template>

<style>
body {
  @apply font-bold font-sans text-sm tracking-wide leading-tight selection:text-stone-500;
}

.intro p {
  @apply my-3 font-sans;
}
</style>