<template>
  <div>
    <ul class="blog-list">
      <li v-for="(item, index) in blogs" class="blog-list__item" :key="item.key">
        <a :href="item.path">{{item.title}}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "blog-list",
  props: {
    pages: {
      type: Array,
      default: []
    }
  },
  data() {
    return {
      blogs: this.filterBlogs(this.pages)
    }
  },
  methods: {
    filterBlogs(list) {
      return list.filter(item => item.type === 'post')
        .sort((x, y) => {
          return new Date(y.frontmatter.date).getTime() - new Date(x.frontmatter.date).getTime()
        })
    }
  }
};
</script>

