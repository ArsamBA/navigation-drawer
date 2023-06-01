<template>
   <div>
      <SideNavigation :navigationData="navigationData" />
      <slot />

   </div>
</template>

<script setup lang="ts">
const navigationData = ref({
   image_url: 'https://avatars.githubusercontent.com/u/104560377?v=4',
   image_alt: 'Arsam',
   name: 'Arsam',
   navLink: [
      {
         path: '/',
         name: 'Home',
         icon : '',

      },
      {
         path: '/blog',
         name: 'Blog',
         icon : '',

      },
      {
         path: '/about',
         name: 'About',
         icon : '',

      },
      {
         path: '/contact',
         name: 'Contact',
         icon : '',

      }
   ],
})
</script>

<style>

</style>