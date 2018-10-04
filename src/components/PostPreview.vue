<template>
  <section class="section container">
    <h1 class="title has-text-centered">
      Recent Posts
    </h1>
    <div class="columns is-multiline">
      <div class="column is-4" v-for="post in posts">
        <nuxt-link :to="{ name: 'posts-slug', params: { slug: post.fields.slug }}">
          <div class="card">
            <header class="card-header">
              <img :src="'https:'+post.fields.heroImage.fields.file.url" style="width:200px; height:300px;" class="card-header-title" />
            </header>
            <div class="card-content">
              <div class="content">
                <small>{{ post.fields.publishData }}</small>
                <h2>{{ post.fields.title }}</h2>
                <div class="tags">
                  <span v-for="tag in post.fields.tags" class="tag is-rounded">{{ tag }}</span>
                </div>
              </div>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    name: "PostPreview",
    props: ['posts']
  }
</script>

<style>
  .content h2 {
    margin-top: 0.2em !important;
  }
</style>
