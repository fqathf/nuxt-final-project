<template>
  <div class="container py-5">
    <div class="form">
      <b-form class="mt-5" @submit="onSubmit" @reset="onReset" v-if="show">
        <b-form-group id="input-group-2" label="Title:" label-for="input-2">
          <b-form-input
            id="input-2"
            v-model="form.title"
            placeholder="Enter title"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-2" label="Author:" label-for="input-2">
          <b-form-input
            id="input-2"
            v-model="form.author"
            placeholder="Enter author"
            required
          ></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-2" label="Content:" label-for="input-2">
          <b-form-textarea
            id="textarea"
            v-model="form.content"
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
            v-model="form.img"
            placeholder="Enter image address"
            required
          ></b-form-input>
        </b-form-group>

        <b-button type="submit" variant="primary">Submit</b-button>
        <b-button type="reset" variant="danger">Reset</b-button>
      </b-form>
      <b-card class="mt-3" header="Form Data Result">
        <pre class="m-0">{{ form }}</pre>
      </b-card>
    </div>
    <div class="container pt-5 row mx-5">
      <CardArticleAdmin
        class="col-4 col-md-4"
        v-for="(article, i) in resultQuery"
        :key="i"
        :article="article"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        title: '',
        author: '',
        content: '',
        img: '',
      },
      show: true,
      articles: [],
    }
  },
  computed: {
    resultQuery() {
      return this.articles
    },
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    async fetchData() {
      try {
        const result = await this.$axios.get('/rest/v1/articles', {
          headers: {
            apikey:
              process.env.SUPABASE_ANON_KEY,
          },
        })
        console.log(result)
        this.articles = result.data
      } catch (error) {
        console.log(error)
      }
    },
    async onSubmit(event) {
      event.preventDefault()
      alert(JSON.stringify(this.form))
      try {
        const result = await this.$axios.post('/rest/v1/articles', this.form, {
          headers: {
            apikey:
              process.env.SUPABASE_ANON_KEY
            },
        })
        console.log(result)
        //this.articles = result.data
      } catch (error) {
        console.log(error)
      }
    },
    onReset(event) {
      event.preventDefault()
      // Reset our form values
      this.form.title = ''
      this.form.author = ''
      this.form.content = ''
      this.form.img = ''
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    },
  },
}
</script>
