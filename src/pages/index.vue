<template>
  <div>
    <section class="hero is-medium is-primary is-bold">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">
            Welcome to the JavaScript SSR Blog.
          </h1>
          <h2 class="subtitle">
            Hope you find something you like.
          </h2>
        </div>
      </div>
    </section>
    <PostPreview :posts="posts"></PostPreview>
  </div>
</template>

<script>
import PostPreview from '~/components/PostPreview.vue'
import {createClient} from '~/plugins/contentful.js'

const client = createClient()

export default {
  head: {
    title: 'Home'
  },
  components: {
    PostPreview
  },
  data () {
    return {
      posts: []
    }
  },
  asyncData ({ env }) {
    return client.getEntries({
      'content_type': 'title',
      // order: '-fields.publishDate',
      'limit': 3
    }).then(entries => {
      return {
        posts: entries.items
      }
    }).catch(console.error)
  }
  // asyncData ({env}) {
  //   return Promise.all([
  //     // fetch the owner of the blog
  //     client.getEntries({
  //       'sys.id': 'EM0DB7AQFiQAwkm86euo0'
  //     }),
  //     // fetch all blog posts sorted by creation date
  //     client.getEntries({
  //       'content_type': 'Blog Post',
  //       order: '-sys.createdAt'
  //     })
  //   ]).then(([entries, posts]) => {
  //     // return data that should be available
  //     // in the template
  //     return {
  //       person: entries.items[0],
  //       posts: posts.items
  //     }
  //   }).catch(console.error)
  // }
}
</script>

<style>

  .main-content {
    margin: 30px 0;
  }

.title {
  /*font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; !* 1 *!*/
  /*display: block;*/
  /*font-weight: 300;*/
  /*font-size: 100px;*/
  /*color: #35495e;*/
  /*letter-spacing: 1px;*/
}

/*.subtitle {*/
  /*font-weight: 300;*/
  /*font-size: 42px;*/
  /*color: #526488;*/
  /*word-spacing: 5px;*/
  /*padding-bottom: 15px;*/
/*}*/


</style>

