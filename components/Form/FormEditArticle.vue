<template>
  <div>
    <div v-for="article in article" :key="article.id">
      <div v-if="article.id == paramid">
        <div class="row">
            <h1 class="col-8">Edit {{ article.title }}</h1>
            <b-button to="/admin/adminaccess/articleadmin" variant="secondary">Back</b-button>
        </div>
        <div class="d-block text-center text-dark">
          <div class="d-block text-dark form">
            <b-form
              class="mt-5"
              @submit.prevent="onEdit(article.id)"
              @reset="onReset"
              v-if="show"
            >
              <b-form-group
                id="input-group-2"
                label="Title:"
                label-for="input-2"
              >
                <b-form-input
                  id="input-2"
                  v-model="formEdit.title"
                  placeholder="Enter title"
                  required
                ></b-form-input>
              </b-form-group>

              <b-form-group
                id="input-group-2"
                label="Author:"
                label-for="input-2"
              >
                <b-form-input
                  id="input-2"
                  v-model="formEdit.author"
                  placeholder="Enter author"
                  required
                ></b-form-input>
              </b-form-group>

              <b-form-group
                id="input-group-2"
                label="Content:"
                label-for="input-2"
              >
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
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      formEdit: {
        title: this.article.title,
        author: this.article.author,
        content: this.article.content,
        img: this.article.img,
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
      default() {},
    },
    paramid: {
      type: String,
      default: '',
    }
  }, 
  methods: {
    async onEdit(id) {
      console.log(id)
      try {
        const result = await this.$axios.patch(
          `/rest/v1/articles?id=eq.${id}`,
          this.formEdit,
          {
            headers: {
              apikey: process.env.SUPABASE_ANON_KEY,
            },
          }
        )
        this.$router.push("/admin/adminaccess/articleadmin")
        window.location.reload()
        /*$router.push*/
      } catch (error) {
        console.log(error)
      }
    },
  }
}
</script>
