<template>
    <main class="container">
      <div class="content" v-if="!$apollo.loading">
        <h1 class="heading-1">{{ page.data.attributes.Titre }}</h1>
        <div v-if="page.data.attributes.Texte" id="editor" v-html="$md.render(page.data.attributes.Texte)" class="content__text content__text--bigger"></div>
      </div>
      <div class="content">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2893.28514246075!2d-1.5049872542066132!3d43.51724627365125!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd5141fb278a1185%3A0x52554bd95b10dc2c!2sNelly&#39;s!5e0!3m2!1sfr!2sfr!4v1658667325882!5m2!1sfr!2sfr" width="100%" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
      </div>
    </main>
</template>

<script>
import pageQuery from "~/apollo/queries/page/page";

export default {
  name: 'ContactPage',
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
        return { "id": 3 };
      },
    },
  },
}
</script>
