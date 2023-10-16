<template>
  <div class="pt-5">
    <div class="container mt-5">
      <FormEditArticle :article="articles" :id="articles.id" :paramid="paramId" />  
      <!--div v-for="article in articles" :key="article.id">
        <div v-if="article.id == paramId">
          <h1>Edit {{ article.title }}</h1>
          <div class="d-block text-center text-dark">
            <div class="d-block text-dark form">
              <b-form
                class="mt-5"
                @submit.prevent="onEdit(id)"
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
      </div-->
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      paramId: this.$route.params.id,
      articles: [],
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    async fetchData() {
      try {
        const result = await this.$axios.get('/rest/v1/articles', {
          headers: {
            apikey: process.env.SUPABASE_ANON_KEY,
          },
        })
        console.log(result)
        this.articles = result.data
      } catch (error) {
        console.log(error)
      }
    },
    tesParam() {
        console.log(this.paramId)
    }
    /*async onEdit(id) {
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
        $router.push
      } catch (error) {
        console.log(error)
      }
    },*/
  },
}
</script>
