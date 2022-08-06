<template>
    <div>
        <div class="socials">
            <a v-bind:href="widget.data.attributes.Facebook" target="_blank" rel="noopenner nofollow noreferrer">
                <svg xmlns="http://www.w3.org/2000/svg" width="20.666" height="20.665" viewBox="0 0 20.666 20.665">
                    <g transform="translate(-1232.806 -6022.499)">
                        <path d="M1243.139,6022.5a10.333,10.333,0,1,0,10.333,10.332A10.333,10.333,0,0,0,1243.139,6022.5Zm2.671,10.331h-1.693l0,6.2h-2.323v-6.2h-1.55v-2.136h1.55l0-1.258c0-1.744.473-2.8,2.525-2.8h1.71v2.137h-1.069c-.8,0-.838.3-.838.855l0,1.07h1.922Z" fill="#000000"></path>
                    </g>
                </svg>                
            </a>
            <a v-bind:href="widget.data.attributes.Instagram" target="_blank" rel="noopenner nofollow noreferrer">
                <svg xmlns="http://www.w3.org/2000/svg" width="20.666" height="20.665" viewBox="0 0 20.666 20.665">
                    <path d="M1211.659,6030.84a1.992,1.992,0,1,0,1.992,1.992A1.993,1.993,0,0,0,1211.659,6030.84Zm4.848-.649a2.21,2.21,0,0,0-2.207-2.207h-5.282a2.209,2.209,0,0,0-2.206,2.207v5.281a2.209,2.209,0,0,0,2.206,2.207h5.282a2.21,2.21,0,0,0,2.207-2.207h0Zm-4.848,5.678a3.038,3.038,0,1,1,3.037-3.037A3.041,3.041,0,0,1,1211.659,6035.869Zm3.707-5.652a.767.767,0,1,1,.225-.542A.774.774,0,0,1,1215.366,6030.217Zm-3.707-7.718a10.333,10.333,0,1,0,10.333,10.332A10.333,10.333,0,0,0,1211.659,6022.5Zm5.894,12.973a3.257,3.257,0,0,1-3.253,3.253h-5.282a3.256,3.256,0,0,1-3.252-3.253v-5.281a3.256,3.256,0,0,1,3.252-3.253h5.282a3.257,3.257,0,0,1,3.253,3.253Z" transform="translate(-1201.326 -6022.499)" fill="#000000"></path>
                </svg>
            </a>
        </div>
        <div v-if="widget.data.attributes.Horaires.Texte" id="editor" v-html="$md.render(widget.data.attributes.Horaires.Texte)" class="horaires">
        </div>
    </div>
</template>

<script>
import widgetQuery from "~/apollo/queries/widget/widget";
export default {
  data() {
    return {
      widget: {
        data: [],
      },
      api_url: process.env.strapiBaseUri,
    };
  },
  apollo: {
    widget: {
      prefetch: true,
      query: widgetQuery,
    },
  },
}
</script>