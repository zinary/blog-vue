<template>
  <div id="add-blog">
    <h1>Add new blog post</h1>
    <form v-if="!submitted">
      <label for="title"> Blog Title</label>
      <input v-model.lazy="blog.title" type="text" />
      <label for="title"> Blog Content </label>
      <textarea v-model.lazy="blog.content" type="text" />
      <label> Blog Categoires</label>

      <div id="checkboxes">
        <label>News</label>
        <input type="checkbox" value="News" v-model="blog.categories" />
        <label>personal</label>
        <input type="checkbox" value="personal" v-model="blog.categories" />
        <label>lifestyle</label>
        <input type="checkbox" value="lifestyle" v-model="blog.categories" />
        <label>tech</label>
        <input type="checkbox" value="tech" v-model="blog.categories" />
      </div>
        <select v-model="blog.author"> 
             <option disabled selected value> -- select an option -- </option>
            <option v-for="(author,index) in authors" :key="index"> {{author}}</option>
        </select>
    <button @click.prevent="postdata">Add blog</button>
    </form>
    <div v-if="submitted">
        <h3>Thanks for submitting</h3>
    </div>
    <div id="preview">
      <h3>Preview blog</h3>

      <p>Blog Category :</p>
      <ul>
        <li v-for="(category, index) in blog.categories" :key="index">
          {{ category }}
        </li>
      </ul>
      <p>Blog title : {{ blog.title }}</p>
        <P>Author: {{blog.author}}</P>
      <p>Blog content : </p>
      <p>{{ blog.content }}</p>
      
    </div>
  </div>
</template>

<script>
// eslint-disable-next-line 
const axios = require('axios');
export default {
  data() {
    return {
      blog: {
        content: "",
        title: "",
        categories: [],
        author: ""
      },
      authors: ['walter white','jesse pinkman','saul goodman'],
      submitted: false
    };
  },
  methods: {
      postdata(){
         axios.post("https://ram-s-vue-blog.firebaseio.com/posts.json",this.blog)
         .then(data => {
              console.log(data)
              this.submitted = true
          }
          ).catch(error=> console.log(error));
      }
  },

};
</script>

<style scoped>
#add-blog * {
  box-sizing: border-box;
}
#add-blog {
  margin: 20px auto;
  max-width: 500px;
}
label {
  display: block;
  margin: 20px 0 10px;
}
input[type="text"],
textarea {
  border: 1px solid rgb(91, 158, 247);
    max-width: 100%;
  display: block;
  width: 100%;
  padding: 8px;
}
#preview {
  padding: 10px 20px;
  border: 1px dotted #ccc;
  margin: 30px 0;
}
h3 {
  margin-top: 10px;
}
#checkboxes input {
  display: inline-block;
  margin-right:20px ;

}
#checkboxes label {
  display: inline-block;
}
h1 {
  text-align: center;
}
</style>
