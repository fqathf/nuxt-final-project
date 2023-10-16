<template>
  <div>
    <b-card
      :title="article.title"
      :img-src="article.img"
      :article="article"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem"
      class="mb-2 text-dark"
    >
      <b-card-text>
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </b-card-text>

      <b-button :to="'/article/' + article.id" href="#" variant="primary"
        >Visit</b-button
      >
      <b-button
        id="show-btn-edit"
        :to="'/admin/adminaccess/articleadmin/' + id"
        variant="secondary"
        >Edit</b-button
      >
      <ModalEditArticle :id="article.id" :article="article" />
      <b-button id="show-btn-delete" @click="onDelete(id)" variant="danger"
        >Delete</b-button
      >
      <ModalDeleteArticle :id="article.id" />
    </b-card>
  </div>
</template>
<script>
export default {
  data() {
    return {}
  },
  props: {
    id: {
      type: String,
      default: '',
    },
    article: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  computed: {
    localTask: {
      get() {
        return this.article
      },
      set(newValue) {
        this.$emit('update:article', newValue)
      },
    },
  },
  methods: {
    async onDelete(id) {
      console.log(id)
      try {
        const result = await this.$axios.delete(
          `/rest/v1/articles?id=eq.${id}`,
          {
            headers: {
              apikey: process.env.SUPABASE_ANON_KEY,
            },
          }
        )
        window.location.reload()
      } catch (error) {
        console.log(error)
      }
    },
    /*console.log(id)
      let deletePrompt = prompt("Type \"" + this.article.title + "\" to delete this article")
      if (deletePrompt == this.article.title) {
        async function confirmDelete(id) {
          
      } else {
        alert("Tidak Sesuai")
      }
    },*/
  },
}
</script>
