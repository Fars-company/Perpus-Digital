<template>
  <div class="visitor text-center">
    <h1>ISI KUNJUNGAN</h1>
    <div class="layer">
      <form class="py-3 m-5" @submit.prevent="addData">
        <div class="row m-3 d-flex justify-content-center">
          <div class="col-sm-10">
            <input v-model="name" class="form-control" type="text" placeholder="Nama ..." aria-label="Nama ..." />
          </div>
        </div>
        <div class="row m-3 justify-content-center">
          <div class="col-sm-10">
            <select v-model="kategori" class="form-control">
              <option disabled value="">Kategori ...</option>
              <option>Siswa</option>
              <option>Guru</option>
              <option>Staf</option>
              <option>Umum</option>
            </select>
          </div>
        </div>
        <div class="row m-3 justify-content-center" v-if="kategori == 'Siswa'">
          <div class="col-sm-3">
            <select v-model="tingkat" class="form-select" aria-label="Disabled select example">
              <option disabled value="">Tingkatan</option>
              <option value="X">X</option>
              <option value="XI">XI</option>
              <option value="XII">XII</option>
            </select>
          </div>
          <div class="col-sm-4 justify-content-center">
            <select v-model="jurusan" class="form-select" aria-label="Disabled select example">
              <option disabled value="">Jurusan</option>
              <option value="TJKT">TJKT</option>
              <option value="TBSM">TBSM</option>
              <option value="PPLG">PPLG</option>
              <option value="DKV">DKV</option>
              <option value="TOI">TOI</option>
            </select>
          </div>
          <div class="col-sm-3 justify-content-center">
            <select v-model="kelas" class="form-select" aria-label="Disabled select example">
              <option disabled value="">Kelas</option>
              <option value="1">1</option>
              <option value="2">2</option>
              <option value="3">3</option>
              <option value="4">4</option>
            </select>
          </div>
        </div>
        <div class="row m-3 justify-content-center">
          <div class="col-sm-10">
            <select v-model="keperluan" class="form-control mb-3">
              <option disabled value="">Keperluan ...</option>
              <option>Membaca</option>
              <option>Meminjam Buku</option>
              <option>Berkunjung</option>
              <option>Mengembalikan Buku</option>
              <option>Lainnya</option>
            </select>
            <input v-if="keperluan == 'Lainnya'" v-model="keperluanLain" class="form-control" type="text" placeholder="Keperluan...">
          </div>
        </div>
        <input type="submit" class="btn" :disabled="isDisabled" value="Kirim">
      </form>
    </div>
  </div>
  <div class="loader"></div>
</template>

<script setup>
const supabase = useSupabaseClient();
const name = ref("");
const kategori = ref("");
const keperluan = ref("");
const keperluanLain = ref("");
const tingkat = ref("");
const jurusan = ref("");
const kelas = ref("");
const dariKelas = ref("");

async function addData() {
  dariKelas.value = `${tingkat.value} ${jurusan.value} ${kelas.value}`;
  const { error } = await supabase.from("kunjungan").insert([
    {
      nama: name.value,
      kategori: kategori.value,
      kelas: dariKelas.value,
      keperluan: keperluan.value == 'Lainnya' ? keperluanLain.value : keperluan.value,
    },
  ]);
  if (error) throw error;
  else navigateTo("/visit");
}

const isDisabled = computed(() => {
  return !name.value || !kategori.value || !keperluan.value
})

</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,600;1,500&family=Playpen+Sans:wght@700&display=swap");
.visitor {
  background-color: #ffffff;
  height: 600px;
}
.row {
  width: 80%;
  padding-top: 2%;
  padding-left: 20%;
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
.btn {
  width: 80px;
  height: 40px;
  background-color: rgb(31, 86, 206);
  color: #ffffff;
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
h1 {
  text-align: center;
  padding-top: 5%;
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
</style>
