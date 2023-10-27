<template>
  <div class="row">
    <div class="col">
      <div class="visitor">
    <h1>VISITOR BOOK</h1>
    <form @submit.prevent="addData" >
            <div class="row">
                <div class="col-sm-10">
                    <input v-model="name" type="text" class="form-control form-control-lg" id="name" placeholder="Nama..." required>
                </div>
            </div>
            <div class="row">
                <div class="col-sm-10">
                    <input v-model="kategori" type="text" class="form-control form-control-lg" id="kategori" placeholder="Kategori..." required>
                </div>
            </div>
            <div class="row">
                <div class="col-sm-10">
                    <input v-model="keperluan" type="text" class="form-control form-control-lg" id="keperluan" placeholder="Keperluan..." required>
                </div>
            </div>  
            <button class="btn">Send</button>
        </form>
  </div>
    </div>
  </div>
</template>

<script setup>
const name=ref('')
const supabase=useSupabaseClient()
const kategori=ref('')
const keperluan=ref('')
async function addData(){
  const {error}=await supabase
  from ('kunjungan')
  .insert=([{
    nama : name.value,
    kategori : kategori.value,
    keperluan : keperluan.value
  }])
}

</script>


<style scoped>
.visitor{
  background-color: #B4C4DB;
  padding-top: 5%;
  height: 600px;
}
h1{
  text-align: center;
}
.row{
  margin:20px;
}

.btn{
    width: 80px;
    height: 40px;
    background-color: #ffffff;
}
</style>