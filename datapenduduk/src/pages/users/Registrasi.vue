<template>
  <q-layout class="bg-blue-grey-1" view="hHh Lpr lFf">
    <q-page-container>
      <q-page padding class="row items-center justify-center">
        <div class="row full-width">
          <div class="col-md-8 offset-md-2 col-xs-12 q-pl-md q-pr-md q-pt-sm">
            <q-card flat class="bg-yellow-8 text-black">
              <div class="row">
                <q-card-section class="text-blue-grey-14">
                  <div class="text-h4">MENU REGISTRASI APLIDES</div>
                </q-card-section>
                <div class="col-md-12 col-xs-6 q-pt-md">
                  <div class="q-pa-md">

                    <q-form
                      @submit="onSubmit"
                      @reset="onReset"
                      class="q-gutter-md"
                    >
                      <q-input
                        filled
                        type="namalengkap"
                        v-model="namalengkap"
                        label="Nama Lengkap"
                        hint="Masukan Nama Lengkap"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />

                      <q-input
                        filled
                        v-model="username"
                        label="Username"
                        hint="Masukan Username Anda"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />
                      <q-input
                        filled
                        type="password"
                        v-model="password"
                        label="Password"
                        hint="Masukan Password Anda"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />

                      <q-input
                        filled
                        v-model="email"
                        label="Email"
                        hint="Masukan Email Anda"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />

                      <q-input
                        filled
                        v-model="nomorhandphone"
                        label="Nomor Handphone"
                        hint="Masukan Nomor Handphone Anda"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />

                      <q-input
                        filled
                        v-model="jeniskelamin"
                        label="Jenis Kelamin"
                        hint="Masukan Jenis Kelamin Anda"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />

                      <q-input
                        filled
                        v-model="agama"
                        label="Agama"
                        hint="Masukan Agama Anda"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />

                      <q-input
                        filled
                        v-model="nomoridentitas"
                        label="Nomor Identitas"
                        hint="Masukan Nomor Identitas Anda"
                        lazy-rules
                        :rules="[ val => val && val.length > 0 || 'Data tidak boleh kosong!']"
                      />

                      <div>
                        <q-btn label="Registrasi" type="submit" color="primary"/>
                        <q-btn label="Login" to="/auth/login" color="primary" flat class="q-ml-sm" />
                      </div>
                    </q-form>

                  </div>
                </div>
              </div>
            </q-card>
          </div>
        </div>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'Registrasi',
  data () {
    return {
      namalengkap: null,
      username: null,
      password: null,
      email: null,
      nomorhandphone: null,
      jeniskelamin: null,
      agama: null,
      nomoridentitas: null,
      accept: false
    }
  },

  methods: {
    onSubmit () {
      if (this.accept !== true) {
        this.$q.notify({
          color: 'red-5',
          textColor: 'white',
          icon: 'warning',
          message: 'You need to accept the license and terms first'
        })
      } else {
        this.$q.notify({
          color: 'green-4',
          textColor: 'white',
          icon: 'cloud_done',
          message: 'Submitted'
        })
      }
    },

    onReset () {
      this.name = null
      this.age = null
      this.accept = false
    }
  }
}
</script>

<style scoped>

</style>
