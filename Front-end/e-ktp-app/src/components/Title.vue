<template>
    <div>
        <div>
            <h3 class="mt-4 shadow title" v-show="Title == '/home'">Homepage</h3>
            <h3 class="mt-4 shadow title" v-show="Title == '/addkk'">Tambah Kartu Keluarga</h3>
            <h3 class="mt-4 shadow title" v-show="Title == '/anggota'">Daftar Anggota Keluarga</h3>
            <h3 class="mt-4 shadow title" v-show="Title == `DetailKK`">Detail KK</h3>
            <h3 class="mt-4 shadow title" v-show="TitleId == `DetailAnggota`">Detail Anggota Keluarga</h3>
        </div>
    </div>
</template>

<script>
export default {
    name: "TitleS",
    data() {
        return {
            Title: this.$route.path,
            TitleId: this.$route.name,
        }
    }
}
</script>

<style scoped>
.title {
    padding: 10px 10px;
    border-radius: 15px;
    background-color: rgb(255, 255, 255);
    margin-left: 10px;
    color: #EB455F;
}
</style>