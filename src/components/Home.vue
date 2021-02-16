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
        <b-button type="is-primary">Generate</b-button>
      </b-field>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      html: null,
      format: 'Letter',
      formats: ['Letter', 'Legal', 'Tabloid', 'Ledger', 'A0', 'A1', 'A2', 'A3', 'A4', 'A5', 'A6']
    }
  }
}
</script>
