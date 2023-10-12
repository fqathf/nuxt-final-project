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
      <b-button id="show-btn-edit" @click="$bvModal.show('bv-modal-edit')" variant="secondary">Edit</b-button>
      <ModalEditArticle :id="article.id" />
      <b-button id="show-btn-delete" @click="$bvModal.show('bv-modal-delete')" variant="danger">Delete</b-button>
      <ModalDeleteArticle :id="article.id" />
    </b-card>
  </div>
</template>
<script>export default {
  props: {
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
}
</script>
