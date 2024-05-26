<template>
  <form class="app" @submit.prevent>
    <h4>Sozdanie posta</h4>
    <input
      v-bind:value="title"
      @input="title = $event.target.value"
      class="input"
      type="text"
      placeholder="Nazvaniye"
    />
    <input
      v-bind:value="body"
      @input="body - $event.target.value"
      class="input"
      type="text"
      placeholder="Opisanie"
    />
    <button class="btn" @click="crearePost">Sozdat</button>
  </form>
  <div>
    <div class="post" v-for="post in posts">
      <div>
        Nazvaniye: <strong>{{ post.title }}</strong>
      </div>
      <div>
        Opisanie: <strong>{{ post.body }}</strong>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        {
          id: 1,
          title: "Zagolovok 1",
          body: "Opisanie",
        },
        {
          id: 2,
          title: "Zagolovok 2",
          body: "Opisanie",
        },
        {
          id: 3,
          title: "Zagolovok 3",
          body: "Opisanie",
        },
      ],
      title: "",
      body: "",
    };
  },
  methods: {
    crearePost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      };
      this.posts.push(newPost);
    },
  },
};
</script>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
.app {
  padding: 20px;
}
form {
  display: flex;
  flex-direction: column;
}
.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  border: 1px solid teal;
  color: teal;
}
</style>
