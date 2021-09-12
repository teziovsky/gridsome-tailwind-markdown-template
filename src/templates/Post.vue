<template>
  <Layout>
    <article class="mx-auto markdown lg:markdown-xl xl:markdown-2xl">
      <h1>{{ $page.post.title }}</h1>
      <div v-html="$page.post.content"></div>
    </article>
    <hr class="m-4" />
    <p class="mx-4">Tags</p>
  </Layout>
</template>

<script>
export default {
  name: 'Post',
  metaInfo() {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: 'description',
          content: this.$page.post.description,
        },
        {
          name: 'twitter:title',
          content: this.$page.post.title,
        },
        {
          name: 'twitter:description',
          content: this.$page.post.description,
        },
        {
          name: 'twitter:card',
          content: 'summary_large_image',
        },
        {
          name: 'twitter:creator',
          content: '@YourTwitterName',
        },
        {
          name: 'twitter:site',
          content: '@YourTwitterName',
        },
        {
          name: 'og:title',
          content: this.$page.post.title,
        },
        {
          name: 'og:description',
          content: this.$page.post.description,
        },
        {
          name: 'og:image',
          content: this.$static.metadata.baseURL + this.$page.post.og_image.src,
        },
      ],
      link: [
        {
          rel: 'canonical',
          content: this.$static.metadata.baseURL + this.$page.post.path,
        },
      ],
    };
  },
};
</script>

<page-query>
query Post($id: ID!) {
  post(id: $id) {
    title
    path
    content
    description
    og_image
  }
}
</page-query>

<static-query>
query {
  metadata {
   baseURL
  }
}
</static-query>