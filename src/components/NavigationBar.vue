<template>
  <nav>
    <router-link to="/">
      <img :src="icon" alt="SWAC" class="desktop nav-icon"/>
      <img :src="iconMobile" alt="SWAC" class="mobile nav-icon">
    </router-link>
    <div class="right">
      <input id="menu-toggle" type="checkbox" />
      <label class='menu-button-container' for="menu-toggle">
        <div class='menu-button'></div>
      </label>
      <span class="menu anchor-beautify">
        <slot></slot>
      </span>
      <Language/>
    </div>
  </nav>
</template>

<script>
import Language from "@/components/Language.vue";

export default {
  name: "NavigationBar",
  components: {Language},
  props: ['icon', 'iconMobile', 'utils', 'mobile']
}
</script>

<style scoped lang="stylus">

.menu
  display flex
  flex-direction row

.menu-button-container {
  display: none;
  height: 100%;
  width: 30px;
  cursor: pointer;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#menu-toggle {
  display: none;
}

.menu-button,
.menu-button::before,
.menu-button::after {
  display: block;
  background-color: #fff;
  position: absolute;
  height: 4px;
  width: 30px;
  transition: transform 400ms cubic-bezier(0.23, 1, 0.32, 1);
  border-radius: 2px;
}

.menu-button::before {
  content: '';
  margin-top: -8px;
}

.menu-button::after {
  content: '';
  margin-top: 8px;
}

#menu-toggle:checked + .menu-button-container .menu-button::before {
  margin-top: 0px;
  transform: rotate(405deg);
}

#menu-toggle:checked + .menu-button-container .menu-button {
  background: rgba(255, 255, 255, 0);
}

#menu-toggle:checked + .menu-button-container .menu-button::after {
  margin-top: 0px;
  transform: rotate(-405deg);
}

@media (max-width: 700px)
  .menu-button-container
    display: flex;

  .menu
    gap 0
    position: absolute;
    top: 0;
    margin-top: var(--nav-height);
    left: 0;
    flex-direction: column;
    width: 100%;
    justify-content: center;
    align-items: center;

  #menu-toggle:deep() ~ .menu div
    height: 0;
    margin: 0;
    padding: 0;
    border: 0;
    transition: height 400ms cubic-bezier(0.23, 1, 0.32, 1);
    overflow hidden
    width 100%
    text-align center

    & > a
      line-height var(--nav-height)

  #menu-toggle:checked:deep() ~ .menu div
    z-index 100
    border-top: 1px solid #333;
    height: var(--nav-height);
    transition: height 400ms cubic-bezier(0.23, 1, 0.32, 1);

    & > a
      width 100%

  .menu:deep() > div
    display: flex;
    justify-content: center;
    align-items center
    margin: 0;
    padding: 0.5em 0;
    width: 100%;
    background-color: #222;


nav
  display flex
  position fixed
  top 0
  left 0
  right 0
  height var(--nav-height)
  background var(--nav-background-dark)
  backdrop-filter blur(20px)
  align-items center
  justify-content space-between
  padding-left var(--nav-padding)
  padding-right var(--nav-padding)
  z-index 1000
  animation 0.5s ease-out 0s 1 slide-from-top
  transition all 0.3s ease-in-out
  color var(--color-dark)

  @media (max-width: 700px)
    background-color #111

  .nav-icon
    height var(--icon-height)
    filter hue-rotate(0)
    transition filter 3s ease-in-out, transform 0.3s ease-in-out

    &:hover
      filter hue-rotate(360deg)
      transform scale(1.05)

  span
    position relative
    display flex
    gap 30px
    line-height calc(var(--nav-height) - 2px)

    a
      font-size 1.2em
      text-decoration none
      transition color 0.3s ease-in-out
      color var(--a-color-dark)

      &:before
        content attr(data-content)
        color var(--a-color-hover)
        position absolute
        display inline-block
        overflow-x hidden
        width 0
        border-bottom var(--a-color-hover) 4px solid
        transition width 0.3s ease-in-out
        line-height calc(var(--nav-height) - 8px)
        translate 0 3px

      &:hover:before
        width 100%

      &:hover
        color var(--a-color-hover)

    a.chosen
      color var(--a-color-hover)

.right
  display flex
  flex-direction row
  gap 50px
  align-items center

</style>