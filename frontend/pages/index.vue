<template>
  <main class="container">
    <div class="content" v-if="!$apollo.loading">
        <img v-if="page.data.attributes.Image"  :src="api_url + page.data.attributes.Image.data.attributes.url" alt="">
        <div v-if="page.data.attributes.Texte" id="editor" v-html="$md.render(page.data.attributes.Texte)" class="content__text content__text--bigger"></div>
    </div>
  </main>
</template>

<script>
// import VideoPlayer from 'nuxt-video-player'
import pageQuery from "~/apollo/queries/page/page";

//require('nuxt-video-player/src/assets/css/main.css')


export default {
  name: 'IndexPage',
  // components: {
  //     VideoPlayer
  // },
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
        return { "id": 1 };
      },
    },
  },
}
</script>