<template>
    <header class="container">
        <div class="menuNav"  v-bind:class="{ 'shown': showMenu }">
            <button @click="closeMenuBtn" class="closeButton">
                <span></span>
                <span></span>
            </button>
            <div class="menuNav__content">
                <ul class="menuNav__links">
                    <li><NuxtLink to="/carte">Carte</NuxtLink></li>
                    <li><NuxtLink to="/contact">Contact</NuxtLink></li>

                </ul>
            </div>
        </div>
        <button @click="showMenuBtn" class="menuButton">
            <span></span>
            <span></span>
            <span></span>
        </button>
        <NuxtLink to="/">
        <picture>
            <source srcset="~/assets/img/logo-small.webp" type="image/webp" media="(max-width: 767px)">
            <source srcset="~/assets/img/logo-small.png" type="image/png" media="(max-width: 767px)">
            <source srcset="~/assets/img/logo.webp" type="image/webp" media="(min-width: 768px)">
            <source srcset="~/assets/img/logo.png" type="image/png" media="(min-width: 768px)">
            <img src="~/assets/img/logo.png" alt="Nelly's Smash burger Anglet" class="header-logo img-fluid" width="214" height="100">
        </picture>
        </NuxtLink>
        <Socials />
    </header>
</template>

<style scoped>
</style>

<script>
export default {
    data () {
      return {
        showMenu: false
      }
    },
    methods: {
        showMenuBtn () {
            this.showMenu = true
        },
        closeMenuBtn () {
            this.showMenu = false
        }
    },
    watch: {
        '$route' () {
            this.showMenu = false
        }
    },
}
</script>
<style scoped>
.header-logo {
    transform: translateX(25px)
}
</style>