<script setup>
const { data: blogPostList } = useAsyncData('blogPostList', () => {
  return queryContent('/blog').find()
})
console.log(blogPostList)
</script>

<!-- 
  - The following divs and classes are from Bulma, a CSS framework.
  - blogPost is an object that contains the data for a blog post.
  - _path is a special property that contains the path to the blog post, which is used to generate the URL.
  - :key is a special attribute that Vue uses to keep track of which elements are which.
  - class is a special attribute that Vue uses to add classes to an element.
  - v-for is a special attribute that Vue uses to loop over an array.
  - NuxtLink is a special component that Nuxt uses to generate links and to: is a special attribute that Nuxt uses to generate the URL.
  - BlogPostMeta is a component containing properties. Author and date are properties that are passed to us.
  - The styles below are from Bulma, a CSS framework.
 -->

<template>
  <div class="container">
    <section class="articles">
      <div class="column is-8 is-offset-2">
        <div
          v-for="blogPost in blogPostList"
          :key="blogPost._path"
          class="card article"
        >
          <NuxtLink :to="blogPost._path">
            <section class="blog-post-card card article">
              <div class="media">
                <div class="media-content has-text-centered">
                  <h3 class="title article-title has-text-weight-bold">
                    {{ blogPost.title }}
                  </h3>
                  <BlogPostMeta
                    :author="blogPost.author"
                    :date="blogPost.date.published"
                  />
                </div>
              </div>
              <div class="card-content">
                <div class="content article-body is-size-5">
                  {{ blogPost.description }}
                </div>
              </div>
            </section>
          </NuxtLink>
        </div>
      </div>
    </section>
  </div>
</template>

<style>
.blog-post-card {
  padding-top: 2.5rem;
  padding-bottom: 3rem;
}

.blog-post-card .card-content {
  padding: 1rem;
}

.blog-post-card .title {
  margin-bottom: 1rem;
}
</style>
