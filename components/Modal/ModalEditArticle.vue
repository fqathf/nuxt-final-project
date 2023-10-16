<template>
  <b-modal id="bv-modal-edit" hide-footer>
    <template #modal-title> Edit {{ article.title }} </template>
    <div class="d-block text-center text-dark">
      <div class="d-block text-dark form">
        <b-form class="mt-5" @submit.prevent="onEdit(id)" @reset="onReset" v-if="show">
          <b-form-group id="input-group-2" label="Title:" label-for="input-2">
            <b-form-input
              id="input-2"
              v-model="formEdit.title"
              placeholder="Enter title"
              required
            ></b-form-input>
          </b-form-group>

          <b-form-group id="input-group-2" label="Author:" label-for="input-2">
            <b-form-input
              id="input-2"
              v-model="formEdit.author"
              placeholder="Enter author"
              required
            ></b-form-input>
          </b-form-group>

          <b-form-group id="input-group-2" label="Content:" label-for="input-2">
            <b-form-textarea
              id="textarea"
              v-model="formEdit.content"
              placeholder="Enter something..."
              rows="3"
              max-rows="6"
              required
            ></b-form-textarea>
          </b-form-group>

          <b-form-group
            id="input-group-2"
            label="Image Link Address:"
            label-for="input-2"
          >
            <b-form-input
              id="input-2"
              v-model="formEdit.img"
              placeholder="Enter image address"
              required
            ></b-form-input>
          </b-form-group>

          <b-button type="submit" variant="primary">Submit</b-button>
          <b-button type="reset" variant="danger">Reset</b-button>
        </b-form>
      </div>
    </div>
    <b-button class="mt-3" block @click="onClose()"
      >Close Me</b-button
    >
  </b-modal>
</template>
<script>
export default {
  data() {
    return {
      formEdit: {
        title: `this.article.title`,
        author: `this.article.author`,
        content: `this.article.content`,
        img: `this.article.img`,
      },
      show: true,
    }
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
  methods: {
    async onEdit(id) {
      console.log(id)
      try {
        const result = await this.$axios.patch(`/rest/v1/articles?id=eq.${id}`, this.formEdit, {
            headers: {
                apikey: process.env.SUPABASE_ANON_KEY
            }
        })
        window.location.reload()
      } catch (error) {
        console.log(error)
      }
    },
    onClose() {
      window.location.reload()
    }
  }
}
</script>
