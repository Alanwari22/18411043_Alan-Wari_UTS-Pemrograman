<template>
  <q-page>
    <div class="q-pa-md">
      <q-table
        title="Treats"
        :data="data"
        :columns="columns"
        row-key="id"
        :filter="filter"
        :loading="loading"
      >

        <template v-slot:top>
          <q-btn color="primary" :disable="loading" label="Tambah Data Penduduk" />
          <q-space />
          <q-input borderless dense debounce="300" color="primary" v-model="filter">
            <template v-slot:append>
              <q-icon name="search" />
            </template>
          </q-input>
        </template>

      </q-table>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      loading: false,
      filter: '',
      rowCount: 10,
      columns: [
        {
          name: 'desc',
          required: true,
          label: 'Nomor Kartu Keluarga',
          align: 'left',
          field: row => row.nomorKartuKeluarga,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'nik', align: 'center', label: 'NIK', field: 'nik', sortable: true },
        { name: 'namaLengkap', label: 'Nama Lengkap', field: 'namaLengkap', sortable: true },
        { name: 'tempatDanTanggalLahir', label: 'Tempat Dan Tanggal Lahir', field: 'tempatDanTanggalLahi' },
        { name: 'alamat', label: 'Alamat', field: 'alamat' },
        { name: 'agama', label: 'Agama', field: 'agama' },
        { name: 'status', label: 'Status', field: 'status' },
        { name: 'jenisKelamin', label: 'Jenis Kelamin', field: 'jenisKelamin' }
      ],
      data: [
        {
          nomorKartuKeluarga: '1806xxxxx',
          nik: 1806262204000001,
          namaLengkap: Alan Wari,
          tempatDanTanggalLahir: Air Naningan 22 April 2000,
          alamat: Balay Rejo,
          agama: 87,
          status: '14%',
          jenisKelamin: '1%'
        }
      ]
    }
  },

  methods: {
    // emulate fetching data from server
    addRow () {
      this.loading = true
      setTimeout(() => {
        const
          index = Math.floor(Math.random() * (this.data.length + 1)),
          row = this.original[Math.floor(Math.random() * this.original.length)]
        if (this.data.length === 0) {
          this.rowCount = 0
        }
        row.id = ++this.rowCount
        const addRow = { ...row } // extend({}, row, { name: `${row.name} (${row.__count})` })
        this.data = [...this.data.slice(0, index), addRow, ...this.data.slice(index)]
        this.loading = false
      }, 500)
    },

    removeRow () {
      this.loading = true
      setTimeout(() => {
        const index = Math.floor(Math.random() * this.data.length)
        this.data = [...this.data.slice(0, index), ...this.data.slice(index + 1)]
        this.loading = false
      }, 500)
    }
  }
}
</script>
