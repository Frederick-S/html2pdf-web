<template>
  <div class="container is-one-third column">
    <section>
      <b-field label="Format">
        <b-select v-model="format">
          <option v-for="format in formats" :value="format" :key="format">{{ format }}</option>
        </b-select>
      </b-field>
      <b-field label="Html">
        <b-input type="textarea" v-model="html"></b-input>
      </b-field>
      <b-field class="is-grouped is-grouped-centered">
        <b-button type="is-primary" @click="generate">Generate</b-button>
      </b-field>
    </section>
  </div>
</template>

<script>
import axios from 'axios'
import fileDownload from 'js-file-download'

export default {
  name: 'Home',
  data () {
    return {
      html: null,
      format: 'Letter',
      formats: ['Letter', 'Legal', 'Tabloid', 'Ledger', 'A0', 'A1', 'A2', 'A3', 'A4', 'A5', 'A6']
    }
  },
  methods: {
    generate () {
      axios.post('https://html2pdf101.azurewebsites.net/pdfs', {
        html: this.html,
        format: this.format
      }, {
        responseType: 'blob'
      }).then(response => {
        fileDownload(response.data, 'generated.pdf')
      }).catch(error => {
        console.error(error)
      })
    }
  }
}
</script>
