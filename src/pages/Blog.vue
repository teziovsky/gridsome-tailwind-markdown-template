<template>
  <Layout>
    <h1 class="text-xl mb-10">Welcome to your Blog!</h1>
    <div class="lg:grid lg:grid-flow-row lg:grid-cols-2 lg:gap-8 lg:auto-rows-auto">
      <div
        v-for="(edge, index) in $page.posts.edges"
        :key="edge.node.id"
        class="prose lg:prose-xl xl:prose-2xl lg:flex lg:flex-col lg:pr-20">
        <a :href="edge.node.path" class="text-green-800 text-xl hover:underline focus:underline">
          <h2>
            {{ edge.node.title }}
          </h2>
        </a>
        <p class="lg:flex-grow lg:justify-self-start">
          {{ edge.node.description }}
        </p>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query Blog {
  posts: allPost (sortBy: "date_published", order: DESC, filter: { published: {eq: true }}){
    edges {
      node {
        id
        title
        description
        tags
        path
        date_published
        timeToRead
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Blog',
  },
};
</script>