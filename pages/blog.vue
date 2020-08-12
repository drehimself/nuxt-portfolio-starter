<template>
  <div class="container-inner mx-auto py-16">
    <div v-for="(post,index) in posts" :key="index" class="post border-gray-400 border-b mb-12">
      <h2 class="text-3xl font-bold"><nuxt-link :to="`/posts/${post.slug}`" class="text-copy-primary">{{ post.title }}</nuxt-link></h2>
      <div class="text-copy-secondary mb-4">
        <span>{{ formatDate(post.date) }}</span>
      </div>

      <div class="text-lg mb-4">
        {{ post.summary }}
      </div>

      <div class="mb-8">
        <nuxt-link :to="`/posts/${post.slug}`" class="font-bold uppercase">Read More</nuxt-link>
      </div>
    </div> <!-- end post -->

    <!-- <pagination-posts
      v-if="$page.posts.pageInfo.totalPages > 1"
      base="/blog"
      :totalPages="$page.posts.pageInfo.totalPages"
      :currentPage="$page.posts.pageInfo.currentPage"
    /> -->
  </div>
</template>

<script>
import { format } from 'date-fns'

export default {
  data() {
    return {
      posts: null,
    }
  },
  methods: {
    formatDate (dateToFormat) {
      return format(new Date(dateToFormat), 'MMMM d, Y')
    }
  },
  async fetch() {
    this.posts = await this.$content()
      .sortBy('date', 'desc')
      .fetch()
  }
}
</script>

<style>

</style>
