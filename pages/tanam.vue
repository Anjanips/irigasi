<script setup>
useHead({
    title: "Tanam",
    meta: [
        {
            name: "description",
            content: "Tanam",
        },
    ],
});

const supabase = useSupabaseClient();
const visitors = ref([]);


// Fungsi untuk mengambil data tanam dari Supabase
const getTanam = async () => {
    const { data, error } = await supabase.from("tanam").select("*");
    if (data) {
        // Menambahkan URL gambar ke setiap visitor
        visitors.value = data.map(visitor => {
            const imageUrl = supabase.storage
                .from('img')
                .getPublicUrl(visitor.img);

            return { ...visitor, imgUrl: imageUrl.data.publicUrl };
        });
    } else {
        console.error('Error fetching tanam data:', error);
    }
};


onMounted(() => {
    getTanam();
});
</script>


<template>
    <div class="judul m-5 text-center">
        <h1>REALISASI TANAM </h1>
        <h2>Periode Tanggal 1 Februari s/d 15 Februari 2025</h2>
    </div>
    <div class="table-container">
        <table class="table table-bordered p-5">
            <thead>
                <tr class="table-success text-center">
                    <th>No</th>
                    <th>Bendung</th>
                    <th>Nama Bendung</th>
                    <th>Luas Layanan (Ha)</th>
                    <th>Faktor K</th>
                    <th>Pengolahan (Ha)</th>
                    <th>Pertumbuhan (Ha)</th>
                    <th>Panen (Ha)</th>
                    <th>Palawija (Ha)</th>
                    <th>Bera (Ha)</th>
                    <th>Kekeringan (Ha)</th>
                    <th>Banjir (Ha)</th>
                    <th>Puso (Ha)</th>
                    <th>Mulai Tanam (bln)</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(visitor, i) in visitors" :key="i">
                    <th scope="row">{{ i + 1 }}.</th>
                    <td><img :src="visitor.img" alt="Visitor Image" width="100" height="100" /></td>
                    <td>{{ visitor.nama_bendung }}</td>
                    <td>{{ visitor.luas_layanan }}</td>
                    <td>{{ visitor.faktork }}</td>
                    <td>{{ visitor.pengolahan }}</td>
                    <td>{{ visitor.pertumbuhan }}</td>
                    <td>{{ visitor.panen }}</td>
                    <td>{{ visitor.palawija }}</td>
                    <td>{{ visitor.bera }}</td>
                    <td>{{ visitor.kekeringan }}</td>
                    <td>{{ visitor.banjir }}</td>
                    <td>{{ visitor.puso }}</td>
                    <td>{{ visitor.mt }}</td>
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