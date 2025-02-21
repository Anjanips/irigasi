<script setup>
useHead({
  title: "Iksi",
  meta: [
    {
      name: "description",
      content: "Iksi",
    },
  ],
});

const supabase = useSupabaseClient();
const visitors = ref([]);
const footerTotals = ref({});

const getIksi = async () => {
  const { data } = await supabase.from("iksi").select("*");
  if (data) visitors.value = data;
};

const getFooterTotals = async () => {
  const { data, error } = await supabase.from("jml_iksi").select("*").single(); 
  if (data) {
    footerTotals.value = data; 
  } else {
    console.error('Error fetching footer totals:', error);
  }
};

onMounted(() => {
  getIksi();
  getFooterTotals(); 
});
</script>


<template>
  <div class="mt-3">
    <h1 class="text-center h4 font-weight-bold mb-4">REKAP IKSI TAHUN 2024</h1>
    <h2 class="text-center h5 mb-3">UPTD PSDA WILAYAH SUNGAI CITANDUY</h2>
    <div class="table-container">
      <table class="table table-bordered">
        <thead class="table-success">
          <tr>
            <th class="text-center">NO.</th>
            <th class="text-center">NAMA DAERAH IRIGASI</th>
            <th class="text-center">KABUPATEN / KOTA</th>
            <th class="text-center">LUAS AREAL (Ha)</th>
            <th class="text-center">Prasarana Fisik</th>
            <th class="text-center">Produktivitas (Padi)</th>
            <th class="text-center">Sarana Penunjang</th>
            <th class="text-center">Organisasi Personalia</th>
            <th class="text-center">Dokumentasi</th>
            <th class="text-center">P3A/GP3A/IP3A</th>
            <th class="text-center">Jumlah</th>
          </tr>
        </thead>
        <tbody>
          <tr class="table-light">
            <td colspan="11" class="text-center">VI UPTD PSDA WS. CITANDUY</td>
          </tr>
          <tr class="table-secondary">
            <!-- <td colspan="11" class="text-center">I SUP Citanduy Hulu</td> -->
          </tr>
          <tr v-for="(visitor, i) in visitors" :key="i">
            <th scope="row">{{ i + 1 }}.</th>
            <td>{{ visitor.nama_daerah }}</td>
            <td>{{ visitor.kabupaten }}</td>
            <td class="text-end">{{ visitor.luas_areal }}</td>
            <td class="text-end">{{ visitor.prasarana }}</td>
            <td class="text-end">{{ visitor.produktivitas }}</td>
            <td class="text-end">{{ visitor.sarana_penunjang }}</td>
            <td class="text-end">{{ visitor.organisasi }}</td>
            <td class="text-end">{{ visitor.dokumentasi }}</td>
            <td class="text-end">{{ visitor.p3a }}</td>
            <td class="text-center">{{ visitor.jumlah }}</td>
          </tr>
        </tbody>
        <tfoot>
          <tr class="table-light">
            <td colspan="3" class="text-center">Jumlah</td>
            <td class="text-end">{{ footerTotals.luas_areal }}</td>
            <td class="text-end">{{ footerTotals.prasarana }}</td>
            <td class="text-end">{{ footerTotals.produktivitas }}</td>
            <td class="text-end">{{ footerTotals.sarana_penunjang }}</td>
            <td class="text-end">{{ footerTotals.organisasi }}</td>
            <td class="text-end">{{ footerTotals.dokumentasi }}</td>
            <td class="text-end">{{ footerTotals.p3a }}</td>
            <td class="text-center">{{ footerTotals.jumlah }}</td>
          </tr>
        </tfoot>
      </table>
      <div class="mt-4 text-end">
        <p class="mb-1">Tasikmalaya, November 2024</p>
        <p class="mb-1">KEPALA UPTD PSDA Wilayah Sungai Citanduy</p>
        <p class="mb-1">Provinsi JAWA BARAT</p>
        <p class="mt-4 fw-bold">MUHAMMAD TAUFIK, S.T., M.E.</p>
        <p>NIP. 19700320 200501 1 000</p>
      </div>
    </div>
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