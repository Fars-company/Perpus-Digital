<template>
  <div class="visitor text-center">
    <h1>ISI KUNJUNGAN</h1>
    <div class="layer">
      <form class="py-3" @submit.prevent="addData" >
        <div class="row-pt justify-content-center">
          <div class="col-sm-10">
              <input v-model="name" type="text" class="form-control form-control-lg" id="name" placeholder="Nama..." required>
          </div>
        </div>
        <div class="row-pt">
          <div class="col-sm-10">
              <input v-model="kategori" type="text" class="form-control form-control-lg" id="kategori" placeholder="Kategori..." required>
          </div>
        </div>
          <div class="row-pt">
            <div class="col-sm-10">
                <input v-model="keperluan" type="text" class="form-control form-control-lg" id="keperluan" placeholder="Keperluan..." required>
            </div>
          </div>  
          <button class="btn">Kirim</button>
      </form>
    </div>
  </div>
</template>

<script setup>
const supabase= useSupabaseClient();
const name= ref('');
const kategori=ref('');
const keperluan=ref('');


async function addData(){
  const {error}=await supabase
  .from ("kunjungan")
  
  .insert([
    {
    nama : name.value,
    kategori : kategori.value,
    keperluan : keperluan.value
    }]);
    if (error) throw error
    else navigateTo('/visit')

}

</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans:ital,wght@0,600;1,500&family=Playpen+Sans:wght@700&display=swap');
.visitor{
  background-color: #ffffff;
  height: 600px;
}
.row-pt{
  width: 90%;
  padding-left:20% ;
  padding-top:3% ;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}
.btn{
  margin-top: 2%;
  width: 100px;
  height: 40px;
  background-color: rgb(31, 86, 206);
  color: #ffffff;
  margin-right: 52%;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
} 
h1{
  text-align: center;
  padding-top: 10%;
  font-family: 'Josefin Sans', sans-serif;
  font-family: 'Playpen Sans', cursive;
}
</style>