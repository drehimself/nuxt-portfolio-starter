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

    <div class="flex justify-between text-xl items-center">
      <a :href="previousPage" :class="{ 'text-gray-400 hover:text-gray-400 cursor-not-allowed': !showPreviousPage }">&larr; Prev</a>
      <div class="text-base">Page {{ currentPage }} of {{ totalPages }}</div>
      <a :href="nextPage" :class="{ 'text-gray-400 hover:text-gray-400 cursor-not-allowed': !showNextPage }">Next &rarr;</a>
    </div>
  </div>
</template>

<script>
import { format } from 'date-fns'

export default {
  data() {
    return {
      posts: [],
      currentPage: 1,
      pagination: 3,
      allPosts: [],
      base: '/blog',
    }
  },
  computed: {
    totalPages() {
      return Math.ceil(this.allPosts.length / this.pagination)
    },
    showPreviousPage() {
      return this.currentPage !== 1
    },
    previousPage() {
      return [0, 1].includes(this.currentPage - 1)
        ? this.base
        : `${this.base}?page=${this.currentPage - 1}`;
    },
    showNextPage() {
      return this.currentPage !== this.totalPages
    },
    nextPage(currentPage, totalPages) {
      return this.totalPages > this.currentPage
        ? `${this.base}?page=${this.currentPage + 1}`
        : `${this.base}?page=${this.currentPage}`;
    }
  },
  methods: {
    formatDate (dateToFormat) {
      return format(new Date(dateToFormat), 'MMMM d, Y')
    }
  },
  async fetch() {
    this.allPosts = await this.$content()
      .fetch()

    this.currentPage = parseInt(this.$route.query.page) ? parseInt(this.$route.query.page) : 1

    if (this.currentPage > this.totalPages) {
      this.$router.push('/blog')
      window.location.href = '/blog'
    }

    this.posts = await this.$content()
      .sortBy('date', 'desc')
      .limit(this.pagination)
      .skip((this.currentPage - 1) * this.pagination)
      .fetch()
  },
  fetchOnServer: false
}
</script>
