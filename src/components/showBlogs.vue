<template>
  <div id="show-blogs">
    <h1>All your blogs</h1>
    <input v-model="search" type="text" placeholder="Search blogs" /> Search
    <div class="single-blog" v-for="blog in filteredBlogs" :key="blog.id">
    <router-link  :to="'/blog/' + blog.id"> <h3>{{ blog.id }}.{{ blog.title | to-uppercase }}</h3>
    </router-link> 
      <article>{{ blog.body | snippet }}</article>
    </div>
  </div>
</template>

<script>
import SearchList from "../mixins/SearchList";
const axios = require("axios");

export default {
  data() {
    return {
      blogs: [],
      search: "",
    };
  },
  methods: {},

  computed: {},
  filters: {
    toUppercase(value) {
      return value.toUpperCase();
    },

    snippet(data) {
      return data.slice(0, 100) + "...";
    },
  },
  directives: {},
  mixins: [SearchList],
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts/")
      .then((response) => {
        console.log(response.data);
        this.blogs = response.data.splice(0, 10);
        console.log(this.blogs);
      });
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
}
#show-blogs {
  max-width: 800px;
  margin: 0 auto;
}
.single-blog {
  padding: 20px;
  margin: 20px 0;
  box-sizing: border-box;
  background-color: #eee;
  transition: 0.5s;
}
input {
  width: 50%;
  height: 30px;
}
</style>
