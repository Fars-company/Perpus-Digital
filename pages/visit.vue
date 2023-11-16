<template>
  <div class="visit">
    <h1>RIWAYAT KUNJUNGAN</h1>
    <NuxtLink to="/" class="btn">Isi kunjungan</NuxtLink>
    <div class="m-2">Menampilkan {{ visitors.length }} data</div>
      <table class="table">
        <thead class="table-primary table-bordered">
          <tr>
            <th>No</th>
            <th>Tanggal</th>
            <th>Nama</th>
            <th>Kategori</th>
            <th>Keperluan</th>
          </tr>
          </thead>
          <tbody class="table-bordered">
            <tr v-for="(kunjungan, index) in visitors" :key="kunjungan.id">
              <td>{{ index + 1 }}</td>
              <td>{{ kunjungan.tanggal }}</td>
              <td>{{ kunjungan.nama }}</td>
              <td>{{ kunjungan.kategori }}</td>
              <td>{{ kunjungan.keperluan }}</td>
            </tr>
        </tbody>
      </table>
</div>

</template>


<script setup>
const supabase = useSupabaseClient();
const visitors = ref([]);


async function getData() {
  const { data, error } = await supabase
  .from("kunjungan")
  .select()
  .order('tanggal',{ascending: false })
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,600;1,500&family=Playpen+Sans:wght@700&display=swap');
.table-bordered{
  width: 96%;
  margin-left: 2%;
  text-align: center;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}
.visit{
  background-color: #ffffff;
  width: 100%;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}
h1{
  text-align: center;
  padding-top: 3%;
  color: rgb(0, 0, 0);
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}
.btn{
  margin: 2%;
  width: 200px;
  height: 40px;
  background-color: rgb(31, 86, 206);
  color: white;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}
</style>