<template>
  <b-modal id="bv-modal-delete" hide-footer>
    <template #modal-title> Delete </template>
    <div class="d-block text-center text-dark">
      <h4>Are you sure to delete this article?</h4>
      <b-button @click="onDelete(id)" variant="danger">Delete</b-button>
    </div>
    <b-button class="mt-3" block @click="$bvModal.hide('bv-modal-delete')"
      >Close Me</b-button
    >
  </b-modal>
</template>
<script>
export default {
  props: {
    id: {
      type: String,
      default: '',
    },
  },
  methods: {
    async onDelete(id) {
      console.log(id)
      try {
        await this.$axios.delete(
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
  },
}
</script>
