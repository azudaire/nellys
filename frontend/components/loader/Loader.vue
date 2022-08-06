<template>
  <div class="preloader" v-if="loading">
  <div class="preloader__brand">
    <picture>
        <source srcset="~/assets/img/logo-small.webp" type="image/webp" media="(max-width: 767px)">
        <source srcset="~/assets/img/logo-small.png" type="image/png" media="(max-width: 767px)">
        <source srcset="~/assets/img/logo.webp" type="image/webp" media="(min-width: 768px)">
        <source srcset="~/assets/img/logo.png" type="image/png" media="(min-width: 768px)">
        <img src="~/assets/img/logo.png" alt="Nelly's Smash burger Anglet" class="img-fluid" width="500" height="234">
    </picture>
  </div>
  </div>
</template>

<style scoped>
  .preloader {
    position: fixed;
    inset: 0 0 0 0;
    background-color: #fdfdfd;
    z-index: 10000;
    opacity: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: opacity 300ms ease;
    width: 100vw;
  }
  .preloader__brand {
      position: absolute;
      transform: translate(-50%, -50%);
      top: 40%;
      left: 50%;
      width: 214px;
      transition: top 500ms cubic-bezier(.14,.38,.49,1.04), left 500ms cubic-bezier(.14,.38,.49,1.04), width 500ms cubic-bezier(0,.56,.07,1.18);
  }
  @media (min-width: 993px) {
    .preloader {
      transition: opacity 300ms ease 700ms;
    } 
    .preloader__brand {
      width: 500px;
    }
  }
</style>

<script>
  export default {
    data: () => ({
      loading: false
    }),
    methods: {
      start() {
        this.loading = true
      },
      finish() {
        this.fadeOut();
        setTimeout(() => {this.loading = false }, 1000)

      },
      fadeOut() {
        document.querySelector('.preloader').style.opacity = 0; 
        if (window.matchMedia("(min-width: 993px)").matches) {
          /* La largeur minimum de l'affichage est 600 px inclus */
          document.querySelector('.preloader__brand').style.top = '66px'; 
          document.querySelector('.preloader__brand').style.left = '50%'; 
          document.querySelector('.preloader__brand').style.width = '214px'; 
        }
      }
    },
    mounted() {
      this.$nextTick(() => {
        this.$nuxt.$loading.start()
        setTimeout(() => this.$nuxt.$loading.finish(), 1000)
      })
    }
  }
</script>