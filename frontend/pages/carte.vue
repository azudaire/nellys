<template>
    <main class="container">
      <div class="content" v-if="!$apollo.loading">
        <div class="carte">
          <h1 class="heading-1">{{ page.data.attributes.Titre }}</h1>
          <dl v-for="item in page.data.attributes.Carte.Plat">
            <dt v-if="item.Nom">{{ item.Nom }} <span class="price" v-if="item.Prix" v-html="item.Prix"></span></dt>
            <dd v-if="item.Description" v-bind:class="{'spec': !item.Nom }" v-html="item.Description"></dd>
          </dl>
          <br>
          <br>
        </div>
        <div class="file">
          <a target="_blank" class="btn" href="img/carte Nelly's.pdf">Télécharger la carte</a>
        </div>
      </div>
      <div class="content" v-if="!$apollo.loading">
        <img v-if="page.data.attributes.Image"  :src="api_url + page.data.attributes.Image.data.attributes.url" alt="Nelly's Smash Burger Anglet">
      </div>
    </main>
</template>

<script>
// import VideoPlayer from 'nuxt-video-player'
import pageQuery from "~/apollo/queries/page/page";

//require('nuxt-video-player/src/assets/css/main.css')


export default {
  name: 'CartePage',
  data() {
    return {
      page: {
        loading: 0,
        data: [],
      },
      api_url: process.env.strapiBaseUri,
    };
  },
  apollo: {
    $loadingKey: 'loading',
    page: {
      prefetch: true,
      query: pageQuery,
      variables() {
        return { "id": 2 };
      },
    },
  },
}
</script>
