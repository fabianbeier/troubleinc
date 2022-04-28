<script setup>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/dist/ScrollTrigger.js";
import { ref, onMounted, onUnmounted } from "vue";

const color = ["text-beige", "text-white", "text-black"];
const background = ["bg-white", "bg-black", "bg-beige"];
const emptyImage = ref([
  {
    src: "/image1.jpg",
    caption:
      "The Other, 2021\n\nCopyright TROUBLE Inc.\nInkjet on CANON Pro Premium Matte, mounted on KROMA® \n81 x 61 cm\n82 x 62 cm framed, Mirogardglass\n1/5 + AP",
  },
  {
    src: "/image2.jpg",
    caption:
      "The Girl With The Door Knocker Earrings, 2021\n\nCopyright TROUBLE Inc.\nInkjet on CANON Pro Premium Matte, mounted on KROMA®\n81 x 61 cm\n82 x 62 cm framed, Mirogardglass\n1/5 + AP",
  },
  {
    src: "/image3.jpg",
    caption:
      "Nirvana, 2021\n\nCopyright TROUBLE Inc.\nInkjet on CANON Pro Premium Matte, mounted on KROMA®\n81 x 61 cm\n82 x 62 cm framed, Mirogardglass\n1/5 + AP",
  },
]);
var num = 0;
let single = ref(color[2]);
let singlebg = ref(background[2]);

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  gsap.from("p, h1, h2", {
    y: 20, // any properties (not limited to CSS)
    opacity: 0, // camelCase
    duration: 1, // seconds
    delay: 3,
    stagger: 0.05,
    ease: "power2.inOut",
  });
  var sections = gsap.utils.toArray(".images");
  sections.forEach((section) => {
    let tl = gsap.timeline({
      scrollTrigger: {
        trigger: section,
        start: "center center",
        scrub: true,
        pin: true,
        pinSpacing: false,
        ease: "power2.Out",
        // pinType: "fixed",
      }, // any properties (not limited to CSS) // camelCase
    });
    tl.addLabel("start")
      .from(section, { scale: 0 })
      .addLabel("color")
      .to(section, {
        scale: 2,
        autoAlpha: 0,
        filter: "blur(60px)",
        onComplete: function () {
          single.value = color[num];
          singlebg.value = background[num];
          // image.value = images[num]
          num++;
          if (num >= color.length) {
            num = 0;
          }
        },
        onReverseComplete: function () {
          single.value = color[num];
          singlebg.value = background[num];
          // image.value = images[num]
          num++;
          if (num >= color.length) {
            num = 0;
          }
        },
      });
  });
});



definePageMeta({
  pageTransition: {
    mode: "default",
  },
});

</script>

<template>
  <div class="relative">
    <div class="">
      <Head>
        <Title>TROUBLE Inc.</Title>
        <Body
          :class="single + ` ` + singlebg"
          class="transition-colors duration-[1000ms]"
        ></Body>
      </Head>
      <div class="p-6 lg:fixed lg:grid grid-cols-2 gap-20 max-w-[1800px]">
        <div class="">
          <div class="text-6xl">
            <h1 class="" @click="test">
              Who is afraid of white, black and beige?
            </h1>
            <p class="text-sm my-5">TROUBLE Inc.</p>
          </div>
          <p class="text-6xl my-10"><a href="#2">28.4 — 3.7.2022</a></p>
          <p>Galerie</p>
          <p>Gisela Clement</p>
          <p>Galeriehaus</p>
          <p class="pt-4">Opening April 28, 2022 at 6pm.</p>
          <p>The exhibition takes place inside the Project Space.</p>
          <p class="pt-4">The artist collective will be present.</p>
          <p>
            On the occasion of the opening there will be an artist talk in
            English led by Prof. Dr. Claudia Jarzebowski.
          </p>
          <p class="pt-4">Lotharstraße 104</p>
          <p>53115 Bonn</p>
          <p class="pb-4">
            <a href="https://galerie-clement.de/">galerie-clement.de</a>
          </p>
        </div>
        <div class="intro">
          <h2 class="italic pt-6 lg:p-0 tracking-wider">Who is afraid of white, black and beige?</h2>
          <p>
            A photographic examination of identity, gender and racism is
            subjected to a complex reinterpretation.
          </p>
          <p>
            What role does skin color plays and how does it still impact our
            feelings and perceptions when making decisions in human
            relationships?
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
            created in this area of ​​tension between our own experiences and
            the lack of representation of the other in our collective memory.
          </p>
          <p class="">
            Michelle Elie (the model-cum-designer-cum-fashion fixture) and Troi
            Ollivierre (the hair and make-up artist) have always been sort of
            creative soulmates. Since their first connection in downtown New
            York City in the '90s, the duo have been creating together, both for
            work and play. Add in Michelle's husband, acclaimed art director and
            artist Mike Meiré, and you have TROUBLE Inc.
          </p>
          <p class="">
            In moments when so many people feel the inequality and injustice of
            the ruling systems, it is about a strong conviction in who you are
            and what you identify with. Without discrimination or exclusion.
            Who's afraid of black, white and beige?
          </p>
          <p
            class="
              pt-4
              text-sm
              my-2
              font-normal
              tracking-widest
              animate-bounce
              opacity-30
            "
          >
            Please Scroll
          </p>
        </div>
      </div>

      <div class="w-full gap-6 p-6 overflow-hidden pointer-events-none">
        <div
          class="w-full rounded overflow-hidden images"
          v-for="(image, index) in emptyImage"
          :key="image"
          :id="index"
        >
          <img
            :src="image.src"
            alt=""
            class="lg:h-screen m-auto rounded overflow-hidden"
          />
          <ClientOnly>
            <caption
              class="w-full block my-2 text-center text-s"
            >
              {{
                image.caption
              }}
            </caption>
          </ClientOnly>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
html{
  scroll-behavior: smooth;
}

body {
  @apply font-bold font-sans tracking-wide leading-tight selection:text-beige-dark;
}

.intro p {
  @apply my-3 font-sans;
}

caption {
  white-space: pre-wrap;
}

</style>