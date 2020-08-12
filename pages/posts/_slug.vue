<template>
  <div>
    <div class="markdown-body">
      <h2>{{ postInMarkdown.title }}</h2>
      <div>{{ dateFormatted }}</div>

      <nuxt-content :document="postInMarkdown" />
      <nuxt-link to="/blog" class="font-bold uppercase">Back to Blog</nuxt-link>

    </div>
  </div>
</template>

<script>
import '~/assets/css/github-markdown.css'
import { format } from 'date-fns'

export default {
  async asyncData ({ $content, params, $axios }) {
    const postInMarkdown = await $content(params.slug)
      .fetch()
      .catch((err) => {
        console.error(err)
      })

    return {
      postInMarkdown
    }
  },
  computed: {
    dateFormatted () {
      return format(new Date(this.postInMarkdown.date), 'MMMM d, Y')
    }
  }
}
</script>

<style>
  .markdown-body {
    box-sizing: border-box;
    min-width: 200px;
    max-width: 980px;
    margin: 0 auto;
    padding: 45px;
  }

  @media (max-width: 767px) {
    .markdown-body {
      padding: 15px;
    }
  }
</style>
