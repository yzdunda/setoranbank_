<template>
  <div id="output-setoran">

    <ul v-for="setoran in dataSetoran" :key="setoran.id">
      <li>
        <span>Nama penyetor: {{setoran.nama}}</span>
        <span>Nominal Setoran: {{setoran.nominal}}</span>
        <span>Keterangan: {{setoran.keterangan}}</span>
      </li>
    </ul>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "outputSetoran",
  data () {
    return {
      dataSetoran: []
    }
  },
  created () {
    axios({
      method: 'get',
      url: 'https://replikasi.herokuapp.com/data/keluaran'
    })
    .then(response => {
      this.dataSetoran = response.data
      console.log(response.statusText) /* eslint-disable-line no-console */
    })
    .catch(err => {
      console.log(err) /* eslint-disable-line no-console */
    })
  }
}
</script>

<style scoped>

ul {
  margin-bottom: 0;
  list-style-type: none;
  border-bottom: 1px solid rgb(128, 128, 128, .5);
}

ul li span {
  display: inline-block;
  width: 100%;
  justify-content: justify;
}

.content blockquote:not(:last-child), .content dl:not(:last-child), .content ol:not(:last-child), .content p:not(:last-child), .content pre:not(:last-child), .content table:not(:last-child), .content ul:not(:last-child) {
  margin: 5px 0;
}
</style>
