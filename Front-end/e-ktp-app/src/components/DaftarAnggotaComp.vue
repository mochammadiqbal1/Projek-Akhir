<template>
    <!-- TABLE START -->
    <table class="table mt-3 table table-striped shadow">
        <thead>
            <tr>
                <th scope="col">No</th>
                <th scope="col">NIK</th>
                <th scope="col">Nama</th>
                <th scope="col">Jenis Kelamin</th>
                <th scope="col">Kepala Keluarga</th>
                <th scope="col">Action</th>
            </tr>
        </thead>
        <tbody v-if="anggotaData.length > 0">
            <tr v-for="(item, index) in anggotaData" :key="index">
                <th scope="row">{{ index + 1 }}</th>
                <td>{{ item.nik }}</td>
                <td>{{ item.nama }}</td>
                <td>{{ item.jenis_kelamin }}</td>
                <td>{{ item.kepala_keluarga }}</td>
                <td>
                    <button class="btn btn-danger" type="submit" @click="deleteAnggota(item.id)">Hapus</button>
                </td>
            </tr>
        </tbody>
        <tbody v-else>
            <tr>
                <td colspan="6">
                    <h4 class="text-center msg-agt">Data Anggota Keluarga Belum Ditambahkan</h4>
                </td>
            </tr>
        </tbody>
    </table>
    <!-- TABLE END -->
</template>

<script>
import anggotaKeluargaServices from '../services/anggotaKeluargaServices'

export default {
    name: 'DaftarAnggotaComp',

    data() {
        return {
            anggotaData: []
        };
    },

    methods: {
        getAll() {
            anggotaKeluargaServices
                .getAll()
                .then((response) => {
                    this.anggotaData = response.data;
                    console.log(this.anggotaData);
                })
                .catch((e) => {
                    console.log(e);
                });
        },

        deleteAnggota(id) {
            if (confirm(`Yakin Ingin menghapus data ini ?`)) {
                anggotaKeluargaServices.deleteAnggotaKeluarga(id)
                    .then((response) => {
                        console.log(response.data);
                        location.reload();
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
        this.getAll()
    }
}
</script>

<style>

</style>