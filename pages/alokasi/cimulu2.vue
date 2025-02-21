<script setup>
useHead({
  title: "Alokasi",
  meta: [
    {
      name: "description",
      content: "Alokasi",
    },
  ],
});

const supabase = useSupabaseClient();
const visitors = ref([]);
const periodeData = ref([]);


// Fungsi untuk mengambil data alokasi
const getAlokasi = async () => {
  const { data } = await supabase.from("alokasi_cimulu").select("*").order("id", { ascending: true });
  if (data) {
    visitors.value = data;
  }
};

// Fungsi untuk mengambil data periode dari database
const getPeriode = async () => {

  const { data, error } = await supabase.from("periode").select("*")
  if (data) {
    periodeData.value = data;
  };
};


// Menghitung jumlah dinamis dari Luas Areal, Realisasi, dan Minggu Ke 1 & 2
const calculateTotal = () => {
  const totalLuas = visitors.value.reduce((acc, visitor) => acc + parseFloat(visitor.luas_areal || 0), 0);
  const totalRealisasi = visitors.value.reduce((acc, visitor) => acc + parseFloat(visitor.realisasi || 0), 0);
  const totalMingguKe1 = visitors.value.reduce((acc, visitor) => acc + parseFloat(visitor.minggu_ke1 || 0), 0);
  const totalMingguKe2 = visitors.value.reduce((acc, visitor) => acc + parseFloat(visitor.minggu_ke2 || 0), 0);

  return { totalLuas, totalRealisasi, totalMingguKe1, totalMingguKe2 };
};

onMounted(() => {
  getAlokasi();
  getPeriode();
});
</script>


<template>
  <div class="judul m-5 text-center">
    <h2>DI CIMULU KAB/KOTA TASIKMALAYA </h2>
    <div v-for="(periode, i) in periodeData" :key="i">
      <h3>{{ periode.judul }}</h3>
    </div>
  </div>

  <div class="table-container">
    <table class="table table-bordered">
      <thead>
        <tr>
          <th scope="col">No</th>
          <th scope="col">Nama Petak Tersier</th>
          <th scope="col">Luas Areal (ha)</th>
          <th scope="col">Realisasi Areal</th>
          <th scope="col">Minggu Ke 1</th>
          <th scope="col">Minggu Ke 2</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(visitor, i) in visitors" :key="i">
          <th scope="row">{{ i + 1 }}.</th>
          <td>{{ visitor.nama_petak }}</td>
          <td>{{ visitor.luas_areal }}</td>
          <td>{{ visitor.realisasi }}</td>
          <td>{{ visitor.minggu_ke1 }}</td>
          <td>{{ visitor.minggu_ke2 }}</td>

        </tr>
        <tr>
          <th scope="row"></th>
          <td><strong>Jumlah Akhir</strong></td>
          <td>{{ calculateTotal().totalLuas.toFixed(2) }}</td> <!-- Menampilkan total luas areal -->
          <td>{{ calculateTotal().totalRealisasi.toFixed(2) }}</td> <!-- Menampilkan total realisasi -->
          <td>{{ calculateTotal().totalMingguKe1.toFixed(2) }}</td> <!-- Menampilkan total minggu ke-1 -->
          <td>{{ calculateTotal().totalMingguKe2.toFixed(2) }}</td> <!-- Menampilkan total minggu ke-2 -->
          <td></td>
        </tr>

      </tbody>
    </table>
  </div>
</template>

<style scoped>
.table-container {
  width: 90%;
  margin: 0 auto;
  font-size: 0.9rem;
}

.table img {
  width: 80px;
  /* Set fixed width for images */
  height: auto;
  object-fit: cover;
}

.table td,
.table th {
  padding: 0.5rem;
  vertical-align: middle;
}

.btn {
  margin-left: 5%;

}
</style>