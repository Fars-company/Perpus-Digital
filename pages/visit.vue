<template>
  <div class="visit">
    <h3>RIWAYAT KUNJUNGAN</h3>
    <NuxtLink to="/" class="btn">Isi kunjungan</NuxtLink>
    <div class="table-responsive">
      <div class="m-2">Menampilkan {{ visitors.length }} data</div>
      <table class="table table-bordered">
        <thead class="text-light">
          <tr>
            <th>No</th>
            <th>Tanggal</th>
            <th>Nama</th>
            <th>Kategori</th>
            <th>Kelas</th>
            <th>Keperluan</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(kunjungan, index) in visitors" :key="kunjungan.id">
            <td>{{ index + 1 }}</td>
            <td>{{ kunjungan.tanggal }}</td>
            <td>{{ kunjungan.nama }}</td>
            <td>{{ kunjungan.kategori }}</td>
            <td>{{ kunjungan.kelas }}</td>
            <td>{{ kunjungan.keperluan }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="loader"></div>
    <h6>Loading</h6>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const visitors = ref([]);

async function getData() {
  const { data, error } = await supabase
  .from("kunjungan")
  .select()
  .order("created_at", { ascending: false });
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,600;1,500&family=Playpen+Sans:wght@700&display=swap");
.table-bordered {
  text-align: left;
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
.visit {
  background-color: #ffffff;
  width: 100%;
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
h3 {
  text-align: center;
  padding-top: 3%;
  color: rgb(0, 0, 0);
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
.btn {
  margin: 1%;
  width: 200px;
  height: 40px;
  background-color: rgb(31, 86, 206);
  color: white;
  font-family: "Josefin Sans", sans-serif;
  font-family: "Playpen Sans", cursive;
}
thead {
  background-color: rgb(31, 86, 206);
}
.loader {
  border: 8px solid #f3f3f3; /* Light grey */
  border-top: 8px solid #3498db; /* Blue */
  border-radius: 50%;
  width: 50px;
  height: 50px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 100px;
  animation: spin 2s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
h6{
  padding-left: 650px;
  margin-top: 10px;
}
</style>
