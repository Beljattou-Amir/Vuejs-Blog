<template>
  <div class="row justify-content-center">
    <form class="col-12 col-lg-8" action="">
      <h2 class="text-white">Ecrivez votre Blog ici</h2>
      <div class="mb-3">
        <textarea  class="form-control text-dark" name="" id="" cols="30" rows="10" placeholder="Mon Blog" v-model="body"></textarea>
      </div>
      <button class="btn btn-success" type="submit" v-on:click.prevent.stop="addPost()"> Partager </button>
    </form>
  </div>
</template>
<script>
import { ref } from "@vue/reactivity";
export default {
  props: ["auth"],
  emits: ["add"],
  setup(props, context) {
    const body = ref("");
    async function addPost() {
      if (body.value) {
        const article = {
          contenu: body.value,
          urlImgArticle: "https://source.unsplash.com/random/1000x300",
          like: 0,
          pseudo: props.auth.user.pseudo,
          date: Date.now(),
          commentaires: []
        };
        const response = await fetch(`http://localhost:3001/articles`, {
          headers: {
            Accept: "application/json",
            "Content-type": "application/json"
          },
          method: "POST",
          body: JSON.stringify(article)
        }).then((resp) => resp.json());
        context.emit("add", response);
        body.value = "";
      }
    }
    return { body, addPost };
  }
};
</script>

<style scoped>
form {
  background: #2c73f7;
  border-radius: 10px;
  padding: 16px 24px;
}
</style>
