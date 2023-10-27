<template>
  <div class="row">
    <div class="col">
      <div class="visit">
    <h1>VISIT LIST</h1>
    <div class="row">
      <div class="col-lg-12">
        <table class="table">
          <thead>
            <tr>
              <th>No</th>
              <th>Tanggal</th>
              <th>Nama</th>
              <th>Kategori</th>
              <th>Keperluan</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(pengunjung, index) in visitors" :key="pengunjung.id">
              <td>{{ index + 1 }}</td>
              <td>{{ pengunjung.tanggal }}</td>
              <td>{{ pengunjung.nama }}</td>
              <td>{{ pengunjung.kategori }}</td>
              <td>{{ pengunjung.keperluan }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
    </div>
  </div>
</template>

<script setup>
const client = useSupabaseClient();
const visitors = ref([]);

async function getData() {
  const { data, error } = await client.from("kunjungan").select();
  if (data) visitors.value = data;
}

onMounted(() => getData());
</script>

<style scoped>
.visit{
  background-color: #273a489a;
  padding-top: 5%;
  height: 600px;
}
h1{
  text-align: center;
  color: white;
}
</style>