<template>
    <div class="container pt-0"> <!-- Mengurangi padding-top di container -->
      <div class="row justify-content-center">
        <div class="col">
          <div id="carouselExampleIndicators" class="carousel slide" data-bs-ride="carousel">
            <!-- Indikator slide -->
            <div class="carousel-indicators">
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="3" aria-label="Slide 4"></button>
              <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="4" aria-label="Slide 5"></button>
            </div>
            
            <!-- Konten gambar carousel -->
            <div class="carousel-inner rounded-5">
              <div class="carousel-item active">
                <img src="assets/img/kantordepan2.jpg" class="d-block w-100" alt="..." />
              </div>
              <div class="carousel-item">
                <img src="assets/img/kantorpsda.jpg" class="d-block w-100" alt="..." />
              </div>
              <div class="carousel-item">
                <img src="assets/img/kantor3.jpg" class="d-block w-100" alt="..." />
              </div>
              <div class="carousel-item">
                <img src="assets/img/0_B. GPI 0-Bendung Gunung Putri.jpg" class="d-block w-100" alt="..." />
              </div>
            </div>
  
            <!-- Tombol navigasi -->
            <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
              <span class="carousel-control-prev-icon rounded-5 bg-secondary" aria-hidden="true"></span>
              <span class="visually-hidden">Previous</span>
            </button>
            <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
              <span class="carousel-control-next-icon rounded-5 bg-secondary" aria-hidden="true"></span>
              <span class="visually-hidden">Next</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  
    <!-- Seksi sambutan -->
    <section class="sambutan-container d-flex align-items-center mt-4">
      <div class="sambutan-wrapper p-4 rounded-4 shadow-sm "> 
        <!-- Foto kepala sekolah -->
        <div class="photo-container me-4"> 
          <img src="assets/img/logopemda.png" alt="Foto Kepala Sekolah" class="photo" />
        </div>
        <!-- Teks sambutan -->
        <div class="text-container">
          <header class="sambutan-header">
            <h1>CAI TEPI SAWAH</h1>
            <h3>UPTD PSDA WS CITANDUY DINAS SUMBER DAYA AIR PROVINSI JAWA BARAT</h3>
          </header>
          <p>
            Capaian Informasi terkait Pengolahan Irigasi pada Wilayah Sungai Citanduy
          </p>
        </div>
      </div>
    </section>
    <div id="profil" class="container">
          <div class="section">
              <h2>Profile</h2>
              <h3>SEKSI IRIGASI CITANDUY</h3>
              <h3>Misi</h3>
              <ul class="list-group-numbered">
                  <li class="list-group-item">Menyiapkan Sumber Daya Manusia yang cerdas dan kompeten baik hardskill maupun softskill.</li>
                  <li class="list-group-item">Meningkatkan dan mengembangkan aktifitas serta kreatifitas seluruh warga sekolah dalam berbagai kegiatan positif.</li>
                  <li class="list-group-item">Mewujudkan manajemen pengelolaan yang efektif, efesien, transparan, akuntabel dan layanan prima.</li>
                  <li class="list-group-item">Menumbuhkan dan mengembangkan potensi dan kemampuan Sumber Daya Manusia yang berdaya saing tinggi melalui berbagai kegiatan akademik maupun non akademik..</li>
                  <li class="list-group-item">Menyelenggarakan berbagai program kegiatan dalam upaya meningkatkan Sumber Daya Manusia yang mampu menyesuaikan dengan perkembangan..</li>
                  <li class="list-group-item">Mengembangkan sarana prasarana dan lingkungan sekolah yang menyenangkan sebagai wadah menumbuhkembangkan daya kreasi dan inovasi untuk menghasilkan produk teknologi tepat guna.</li>
                  <li class="list-group-item">Membangun jiwa wirausaha yang handal melalui pembelajaran Teaching Factory (TEFA) dan Kelas Industri.</li>
                  <li class="list-group-item">Menjalin dan mengembangkan kemitraan dengan Industri dan Dunia Kerja (IDUKA) serta lembaga lainnya yang relevan.</li>
                  <li class="list-group-item">Menanamkan dan membudayakan sikap dan perilaku yang baik pada aktivitas di sekolah maupun dalam kehidupan sehari-hari.</li>
              </ul>
          </div>
      </div>
  
      
  </template>
  
  <style scoped>
  
  .container {
    padding-top: 0; 
  }
  
  
  .carousel-inner {
    width: 100%;
    height: 70vh; 
    overflow: hidden; 
  }
  
  .carousel-inner .carousel-item img {
    width: 80%;
    height:100%;
    object-fit: cover; 
    object-position: center center; 
  }
  
  
  .sambutan-container {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1rem; 
  }
  
  .sambutan-wrapper {
    display: flex;
    align-items: center;
    gap: 1.5rem; 
    background-color: #DEE9EF;
    padding: 1.3rem;
    border-radius: 50px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }
  
  .photo-container {
    flex-shrink: 0;
    width: 200px;
  }
  
  .photo-container img {
    width: 100%;
    border-radius: 10px;
    object-fit: cover;
  }
  
  .text-container {
    flex-grow: 1;
  }
  
  .sambutan-header {
    margin-bottom: 1rem;
  }
  
  .sambutan-header h2 {
    font-size: 1.5rem;
    font-weight: bolder;
    margin-bottom: 1rem;
  }
  
  .sambutan-header h3 {
    font-size: 1.2rem;
    color: #000000;
    margin-bottom: 1rem;
  }
  
  .profile {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: center;
      gap: 20px;
      scroll-behavior: smooth; 
  }
  
  .profile img {
      margin-top: 50px;
      max-width: 300px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  .profile-text {
      margin-top: 50px;
      max-width: 600px;
      text-align: justify;
  }
  
  .section h2 {
      font-size: 50px;
      margin-bottom: 10px; 
      margin-top: 50px; 
      border-bottom: 2px solid #000000; 
      display: block; 
      text-align: center; 
      width: fit-content; 
      margin-left: auto; 
      margin-right: auto; 
      padding-bottom: 5px; 
  }
  
  
  
  .section h3 {
      display: flex;
      justify-content: center; 
      margin-bottom: 30px;
  }
  
  .section p {
      display: flex;
      justify-content: center; 
  }
  </style>

  <!-- <template>
    <table class="table table-bordered">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@fat</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td colspan="2">Larry the Bird</td>
      <td>@twitter</td>
    </tr>
  </tbody>
</table>
</template> -->