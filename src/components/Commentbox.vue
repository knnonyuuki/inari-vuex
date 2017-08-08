<template>
  <div class="comment-box">
    <div class="form">
      <input type="text" id="commentForm">
      <button type="submit" v-on:click="addComment">提交</button>
    </div>
    <ul>
      <li v-for="comment in reversedComments">
        {{comment.text}}
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    name: 'comment-box',
    data: () => ({
      comments: [
        {
          text: 'hi'
        },
        {
          text: 'hello inari'
        }
      ]
    }),
    computed: {
      reversedComments: function () {
        return this.comments.slice().reverse()
      }
    },
    methods: {
      addComment: function () {
        const text = document.getElementById('commentForm').value
        this.comments.push({text})
        document.getElementById('commentForm').value = ''
      }
    }
  }
</script>
<style scoped>
  .form {
    display: flex;
    margin-bottom: 10px;
  }
  button {
    background-color: deeppink;
    color: white;
    border: 0;
    outline: 0;
    line-height: 20px;
    padding: 5px 20px;
    margin: 0 0 0 10px;
  }
  button:hover {
    cursor: pointer;
  }
  input {
    height: 30px;
    line-height: 30px;
    text-indent: 5px;
    display: flex;
    flex-grow: 1;
  }
  .comment-box {
    background-color: #fff;
    box-shadow: 0 1px 2px rgba(0, 0, 0, .5);
    width: 80%;
    margin: 30px auto;
    padding: 20px;
    line-height: 1.8;
  }
</style>

