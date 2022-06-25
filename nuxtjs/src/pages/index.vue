<template>
  <div>
  <h1>記事一覧</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        id: {{ post.id }}<br>
        slug: {{ post.slug }}<br>
        title: {{ post.title.rendered }}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    async asyncData({$axios}) {
      const posts = await $axios.$get('http://wordpress/wp-json/wp/v2/posts')
      return { posts }
    }
  }
</script>