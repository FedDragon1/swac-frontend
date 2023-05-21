<script>
import NavigationBar from "@/components/NavigationBar.vue";

export default {
  name: "App",
  components: {
    NavigationBar
  }
}
</script>

<template>
  <NavigationBar icon="src/assets/images/icon-text-light.png" icon-mobile="/fav-icons/android-chrome-192x192.png">
    <div>
      <router-link class="chosen" to="/" data-content="Home">Home</router-link>
    </div>
    <div>
      <router-link class="hover" to="/course" data-content="Course">Course</router-link>
    </div>
    <div>
      <router-link class="hover" to="/playground" data-content="Playground">Playground</router-link>
    </div>
    <div>
      <router-link class="hover" to="/about" data-content="About">About</router-link>
    </div>
  </NavigationBar>
  <router-view/>
</template>

<style lang="stylus">
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+SC&family=Quicksand&display=swap');
@import "/assets/css/mixins.styl";

@font-face {
  font-family: 'zhuziawan';
  font-style: normal;
  font-weight: 400;
  src: url(/src/assets/zhuziawan.woff2) format('woff2');
}

//global
$background-color = #f0f0f0

// nav
$nav-height = 70px
$icon-height = 30px
$nav-padding = 40px
$nav-background = rgba(white, 0.6)

// text
$a-color = #141414
$a-color-hover = #f4b232
$color = #141414
$accent-color = yellow

//dark mode
$color-dark = #f0f0f0
$a-color-dark = #f0f0f0
$background-color-dark = #141414
$nav-background-dark = rgba(black, 0.6)

:root
  --nav-height $nav-height
  --icon-height $icon-height
  --nav-padding $nav-padding
  --a-color $a-color
  --a-color-hover $a-color-hover
  --color $color
  --accent-color $accent-color
  --background-color $background-color
  --a-color-dark $a-color-dark
  --color-dark $color-dark
  --background-color-dark $background-color-dark
  --nav-background $nav-background
  --nav-background-dark $nav-background-dark


body
  padding 0
  margin 0
  overflow-x hidden
  user-select none
  font-family "Quicksand", "zhuziawan", 'Noto Sans SC'
</style>
