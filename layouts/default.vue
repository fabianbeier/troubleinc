<script lang="ts" setup></script>

<template>
  <div >
    <keep-alive>
    <slot />
    </keep-alive>
    <div class="p-6">
      <ul class="flex gap-3 pt-96 justify-center w-full">
        <!-- <li><nuxt-link to="/">Home</nuxt-link></li> -->
        <!-- <li><nuxt-link to="/imprint">Imprint</nuxt-link></li>
        <li>Legal</li> -->
      </ul>
    </div>
    
  </div>
</template>

<style scoped></style>
