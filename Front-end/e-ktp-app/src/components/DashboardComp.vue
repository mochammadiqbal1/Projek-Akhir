<template>
  <div>
    <div v-show="!success">
      <!-- CARD START -->
      <div class="cards">
        <div class="jkk shadow">
          <p class="text">Jumlah Kartu Keluarga</p>
          <p class="angka">{{ kartuKeluargaData.length }}</p>
        </div>

        <div class="jsw shadow">

          <p class="text">Jumlah Seluruh Warga</p>
          <p class="angka">{{ anggotaKeluargaData.length }}</p>
        </div>
      </div>
      <!-- CARD END -->

      <!-- TABLE START -->
      <table class="table mt-5 table table-striped shadow">
        <thead>
          <tr>
            <th scope="col">No</th>
            <th scope="col">Nomor KK</th>
            <th scope="col">Alamat</th>
            <th scope="col">Kota</th>
            <th scope="col">Kode Pos</th>
            <th scope="col">Action</th>
          </tr>
        </thead>
        <tbody v-if="kartuKeluargaData.length > 0">
          <tr v-for="(item, index) in kartuKeluargaData" :key="index">
            <th scope="row">{{ index + 1 }}</th>
            <td>{{ item.nomor_kk }}</td>
            <td>{{ item.alamat }}</td>
            <td>{{ item.kabupaten_kota }}</td>
            <td>{{ item.kode_pos }}</td>
            <td>
              <!-- BUTTON -->
              <router-link :to="{ path: '/detailKK/' + item.nomor_kk }">
                <button class="btn btn-success" type="submit">Detail</button>
              </router-link>

              <button class="btn btn-danger" type="submit" @click="deleteKK(item.id)">
                Hapus
              </button>
            </td>
          </tr>
        </tbody>
        <tbody v-else>
          <tr class="msg-tr text-center">
            <td colspan="6" class="msg-null">
              <h3>Saat ini Tidak Ada Data Kartu Keluarga !</h3>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <!-- TABLE END -->
    <div v-show="success">
      <Success :propsAlert="textAlert"></Success>
    </div>
  </div>
</template>

<script>
import kartuKeluargaServices from "@/services/kkServices";
import anggotaKeluargaServices from "@/services/anggotaKeluargaServices";
import Success from "./Success.vue";

export default {
  name: "DashboardS",

  data() {
    return {
      kartuKeluargaData: [],
      anggotaKeluargaData: [],
      success: false,
      textAlert: '',
    };
  },

  components: {
    Success
  },

  methods: {
    // METHOD GET ALL DATA KK
    getKK() {
      kartuKeluargaServices
        .getAll()
        .then((response) => {
          this.kartuKeluargaData = response.data;
          console.log(this.kartuKeluargaData);
        })
        .catch((e) => {
          console.log(e);
        });
    },

    // METHOD GET ALL ANGGOTA
    getAnggota() {
      anggotaKeluargaServices
        .getAll()
        .then((response) => {
          this.anggotaKeluargaData = response.data;
          console.log(this.anggotaKeluargaData);
        })
        .catch((e) => {
          console.log(e);
        });
    },

    // METHOD DELETE KK
    deleteKK(id) {
      if (confirm(`Yakin Ingin menghapus data ini ?`)) {
        kartuKeluargaServices
          .deleteKartuKeluarga(id)
          .then((response) => {
            console.log(response.data);
            this.textAlert = 'Dihapus';
            this.success = true;
          })
          .catch((e) => {
            console.log(e);
          });
      } else {
        alert("Hapus Dibatalkan");
      }
    },
  },

  mounted() {
    this.getKK();
    this.getAnggota();
  },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

h2 {
  margin-left: 10px;
}

/* Button */
.btn-success {
  padding: 5px 11px;
  margin-right: 10px;
  background-color: #2B3467;
  border: none;
}

.btn-danger {
  padding: 5px 13px;
  margin-right: 10px;
  border: none;
  background-color: rgb(236, 79, 79);
}



.cards {
  display: flex;
  flex-direction: row;
  margin-top: 25px;
  justify-content: flex-start;
  margin-left: 10px;
}

/* Card Start */
.jkk {
  background-color: #ff566f;
  color: rgb(59, 59, 59);
  margin-right: 40px;
  width: 280px;
  height: 160px;
  padding: 20px 20px;
  border-radius: 10px;
  transition: transform 400ms;
  cursor: pointer;
  color: white;
}


.jsw {
  background-color: #2B3467;
  color: aliceblue;
  width: 280px;
  height: 160px;
  padding: 20px 20px;
  border-radius: 10px;
  cursor: pointer;
}



.jsa {
  background-color: rgb(65, 67, 111);
  color: aliceblue;
  width: 270px;
  height: 150px;
  padding: 20px 20px;
  border-radius: 20px;
}

/* Card End */

table {
  border: 1px solid #f2f2f2;
  margin-left: 10px;
}

.angka {
  font-size: 40px;
  margin-bottom: 5px;
}

.text {
  font-size: 20px;
  margin-top: 10px;
}

.title-table {
  margin-top: 25px;
  margin-left: 15px;
}

h3 {
  color: #EB455F;
}

/* span {
  background-color: rgb(255, 255, 255);
  padding: 5px 5px;
  border-radius: 100%;
} */

.ico-card-2 {
  color: #00df7a;
  background-color: rgb(255, 255, 255);
  padding: 5px 5px;
  border-radius: 100%;
}

.ico-card-1 {
  color: rgb(255, 198, 77);
  background-color: rgb(255, 255, 255);
  padding: 5px 5px;
  border-radius: 100%;
}

.delete {
  font-size: 20px;
}

/*  */
</style>