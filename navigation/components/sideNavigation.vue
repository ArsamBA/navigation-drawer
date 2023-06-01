<template>
   <div class="side-navigation-wrapper">
      <div class="navigation-information">
         <img :src="navigationData.image_url" :alt="navigationData.image_alt" />
         <p v-if="character">{{ navigationData.name }}</p>
         <p v-else>{{ navigationData.name }}...</p>
      </div>
      <div class="navigation-links">
         <nuxt-link v-for="link in navigationData.navLink" :key="link" :to="link.path">
            <span v-html="link.icon"></span>
            <p>
               {{ link.name }}
            </p>   
         </nuxt-link>
      </div>
   </div>
</template>

<script setup lang="ts">
const props = defineProps<{
   navigationData?: any;
}>();
const character  = ref(true)

if(props.navigationData.name.length > 8) {
   character.value = false
} else {
   character.value = true
}

</script>

<style lang="scss">
@import '@/assets/scss/global.scss';
.side-navigation-wrapper {
   position: fixed;
   width: 80px;
   height: calc(100% - 0px);
   border-right: 1px solid #bbafaf;
   transition: 0.5s;
   overflow: hidden;
   &:hover {
      width: 200px;
      transition: 0.5s;

      .navigation-information{
         img {
            width: 70px;
            height: 70px;   
            transition: 0.5s;
         }
      }
   }
}
.navigation-information {
   padding: 15px;
   width: 100%;
   display: flex;
   flex-direction: row;
   align-items: center;
   border-bottom: 1px solid #bbafaf;

   img{
      width: 50px;
      height: 50px;
      border-radius: 50%;
      transition: 0.5s;
   }
   p {
      overflow: hidden;
      max-width: 125px;
      margin-top: 5px;
      margin-left: 15px;
   }
}

.navigation-links {
   padding: 10px 26px;
   display: flex;
   flex-direction: column;
   align-items: flex-start;
   a {
      margin-top: 30px;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      &:nth-child(1){
         margin-top: 15px;
      }
      &:hover {
         p{
            color: $primary;
         }
         span{
            fill: $primary;
         }
      }
      p {
         margin-left: 25px;
      }
   }
}
</style>