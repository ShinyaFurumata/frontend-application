<template>
  <nav class="area-nav" :class="{ 'is-fixed': isFixed }">
    <div class="area-nav-inner">
      <select-paypart-publish-button class="area-post-article" />
    </div>
  </nav>
</template>

<script>
import SelectPaypartPublishButton from '../molecules/SelectPaypartPublishButton'

export default {
  components: {
    SelectPaypartPublishButton
  },
  data() {
    return {
      isFixed: false
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll() {
      this.isFixed = window.scrollY >= 100
    }
  }
}
</script>

<style lang="scss" scoped>
.area-nav {
  background: #fff;
  display: grid;
  grid-area: nav;
  height: 74px;
  text-align: center;
  transition: box-shadow 400ms ease;
  width: 100%;
  z-index: 2001;
  /* prettier-ignore */
  grid-template-areas:
    "nav-inner";

  .area-nav-inner {
    display: grid;
    grid-area: nav-inner;
    grid-template-columns: 1fr min-content;
    margin: auto;
    width: 640px;
    /* prettier-ignore */
    grid-template-areas:
      "... post-article";

    .area-post-article {
      grid-area: post-article;
      border-radius: 4px;
      border-radius: 4px;
      box-shadow: none;
      color: #fff;
      cursor: pointer;
      font-size: 14px;
      font-weight: 100;
      height: 34px;
      line-height: 2.5;
      text-align: center;
      width: 96px;

      &:hover,
      &:focus {
        background: #0086cc;
      }

      &.disable {
        cursor: not-allowed;
      }
    }
  }

  &.is-fixed {
    box-shadow: 0 12px 12px -12px rgba(192, 192, 192, 0.7);
    left: 0;
    position: fixed;
    right: 0;
  }
}

@media screen and (max-height: 414px) {
  .area-nav {
    &.is-fixed {
      position: static;
    }
  }
}

@media screen and (max-width: 640px) {
  .area-nav {
    background: #fff;
    display: grid;
    grid-area: nav;
    height: 74px;
    text-align: center;
    transition: box-shadow 400ms ease;
    width: 100%;
    z-index: 2001;
    /* prettier-ignore */
    grid-template-areas:
      "nav-inner";

    .area-nav-inner {
      display: grid;
      grid-area: nav-inner;
      grid-template-columns: 1fr min-content 12px;
      margin: auto;
      width: 100%;
      /* prettier-ignore */
      grid-template-areas:
        "... post-article ...";
    }
  }
}
</style>
