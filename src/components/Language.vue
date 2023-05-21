<template>
  <span @mouseover="mouseover" @mouseleave="mouseleave" class="align-center" id="lang-container">
    <span @click="toCN" id="chinese" class="text">中</span>
    <span id="dummy"></span>
    <span @click="toEN" id="english" class="text">En</span>
  </span>
</template>

<script>
export default {
  name: "Language",
  data: function() {
    return {
      base: undefined,
      cn: undefined,
      en: undefined,
      bar: undefined,
      rotation: 45,
    }
  },
  methods: {
    toCN() {
      console.log("中文");
    },
    toEN() {
      console.log("English")
    },
    mouseover() {
      if (!this.base) {
        this.base = document.getElementById("lang-container")
        let children = this.base.children;
        this.cn = children.chinese.style;
        this.en = children.english.style;
        this.bar = children.dummy.style;
      }

      this.bar.transform = "rotate(0)";
      this.bar.height = "calc(var(--nav-height) * 0.7)";
      this.bar.bottom = "0";
      this.cn.left = "-2px";
      this.cn.top = "14px";
      this.en.left = "10px";
      this.en.top = "-12px";
    },
    mouseleave() {
      if (!this.base) {
        this.base = document.getElementById("lang-container")
        let children = this.base.children;
          this.cn = children.chinese.style;
          this.en = children.english.style;
          this.bar = children.dummy.style;
      }

      this.bar.transform = `rotate(${(this.rotation += 180) % 360}deg)`;
      this.bar.height = "calc(var(--nav-height) * 0.8)";
      this.bar.bottom = "-4px";
      this.cn.left = "4px";
      this.cn.top = "2px";
      this.en.left = "4px";
      this.en.top = "0";
    }
  }
}
</script>

<style lang="stylus" scoped>
#dummy
  position absolute
  display inline-block
  height calc(var(--nav-height) * 0.8)
  border-right 2px var(--color-dark) solid
  border-radius 50% 50% 50% 50%
  transform rotate(45deg)
  bottom -4px
  left 26px
  transition all 0.2s ease-in-out

#chinese
  position relative
  top 2px
  left 4px
  grid-row 1
  grid-column 1

#english
  position relative
  left 4px
  grid-row 2
  grid-column 2

.text
  line-height normal
  white-space pre-line
  transition all 0.2s ease-in-out

  &:hover
    color var(--a-color-hover)

.align-center
  grid-template-columns: 25px 25px;
  grid-template-rows: 25px 25px;
  display grid
  gap 2px
  position relative
  font-size 20px

</style>